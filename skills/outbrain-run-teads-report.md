---
name: Run an asynchronous Teads analytics report
description: Trigger a Teads Report API job, poll it to completion, download the result, and stay inside the two-concurrent and fifty-per-day quotas.
api: openapi/outbrain-teads-report-api-openapi.yml
operations:
  - createReport
  - getReportStatus
  - listProcessingReports
  - cancelReport
---

# Run a Teads analytics report

Base URL: `https://api.teads.tv/v1/analytics`. This is a **different API from Amplify** — different
host, different auth, different error envelope. Do not carry an `OB-TOKEN-V1` token here.

## 1. Authenticate

```
Authorization: Bearer {OAuth bearer token}
Content-Type: application/json
```

The account needs reporting rights on the Teads platform.

## 2. Trigger the report

`createReport` (`POST /custom`). The body carries `date` (the only required filter), optional
dimension and metric selections, optional `emails`, and a `format` (`csv`, `jsonv1` or `xlsx`).

Period rules — violating any of these returns a `REPORTING.ERROR.*` code, not a generic 400:

- Nothing before **2020** (`PERIOD_NOT_FULLY_AVAILABLE_IN_NEW_REPORTING_ENGINE`).
- Maximum **one year** per report (`REPORT_PERIOD_TOO_LONG`).
- A `uv` report longer than 100 days must include the `day` dimension (`UV_REPORT_PERIOD_TOO_LONG`).
  Note the `uv` flag and the expanded finance metrics were both announced for deprecation from
  2024-01-01.

Filters are id-based (`placements: [1]`). Avoid the `format` filter where you can — Teads warns it is
computationally expensive and can make requests slow or fail.

The response returns `id`, `start`, `status: queued`, `valid` and a `reportProgress` object.

## 3. Poll

`getReportStatus` (`GET /custom/{id}`) until `status` leaves `queued`/`processing`.

| status | meaning |
|---|---|
| `queued` | waiting on Teads capacity |
| `processing` | being computed; `reportProgress` carries `step`/`stepMax`/`progress`/`progressMax` |
| `finished` | done — download from the `url` field |
| `error` | see `message` |
| `killed` | cancelled |

Back off between polls. On `429` the response carries **`Retry-After`** in seconds; the documented
gap between two reports can reach 30 minutes.

## 4. Stay inside the quotas

- **Two** reports may process concurrently — a third returns
  `REPORTING.ERROR.RUNNING_REPORT_QUOTA_REACHED`.
- **50** reports per rolling 24 hours — beyond that,
  `REPORTING.ERROR.PAST_24H_REPORT_QUOTA_REACHED`.

Before triggering, call `listProcessingReports` (`GET /running/list`) to see what is already in
flight. If you need a slot, cancel with `cancelReport` (`PUT /custom/{id}/kill`).

There is no idempotency key: every `POST /custom` consumes quota. Never blind-retry a report request
— poll the id you already have.

## 5. Errors

Envelope is `{"status": 400, "msg": "REPORTING.ERROR.APPLICATION_NOT_FOUND"}`. Field-level validation
failures use a different shape — a map keyed by the JSON path of the bad field, e.g.
`{"obj.dimensions.dimensions.filters.insertions[0]": [{"msg": "error.expected.jsnumber", "args": []}]}`.
Support: `api@teads.tv`.
