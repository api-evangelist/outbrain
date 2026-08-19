---
name: Pull Outbrain Amplify performance reporting
description: Check data freshness, then pull campaign, promoted-content, publisher, section or geo performance for a marketer while staying inside the reporting rate limits.
api: openapi/outbrain-amplify-api-full-openapi.yml
operations:
  - getReportsDataFreshness
  - getReportsFullDay
  - getReportsMarketersIdCampaigns
  - getReportsMarketersIdPromotedContent
  - getReportsMarketersIdPeriodic
  - getReportsMarketersIdPublishers
  - getReportsMarketersIdSections
  - getReportsMarketersIdGeo
  - getReportsAccountsPrimaryAccountIdMarketers
---

# Pull Outbrain Amplify performance data

Base URL: `https://api.outbrain.com/amplify/v0.1`.

## 1. Ask how fresh the warehouse is — first

`getReportsDataFreshness` (`GET /reports/dataFreshness`) and `getReportsFullDay`
(`GET /reports/fullDay`, the last day of complete data). Outbrain publishes no reporting SLA; these
two operations are the contract. Pulling a date range past the freshness boundary returns thin
numbers that will change under you, so clamp `to` to the full-day boundary before you report.

## 2. Choose the slice

All of these take `from`, `to`, `limit`, `offset`, `sort`, `filter`:

| Question | Operation |
|---|---|
| How is each campaign doing? | `getReportsMarketersIdCampaigns` |
| Which creative is working? | `getReportsMarketersIdPromotedContent` |
| How does it trend over time? | `getReportsMarketersIdPeriodic` (`breakdown` = day/week/month) |
| Which publishers deliver? | `getReportsMarketersIdPublishers` |
| Which placements deliver? | `getReportsMarketersIdSections` |
| Where are the users? | `getReportsMarketersIdGeo` |
| Roll up across all accounts | `getReportsAccountsPrimaryAccountIdMarketers` |

The account-level roll-up needs the **primary account id**, which comes from
`GET /marketers/{id}` with `extraFields=Account` — not from `GET /marketers`.

## 3. Set `enabledCampaignsOnly` explicitly

This filter was added 2024-12-22 with a default of `false`, and Outbrain announced the default would
flip to `true` at the end of January 2025. If you do not set it, your result set is defined by a
default that has already moved once. Set it.

For historical comparisons also set `includeArchivedCampaigns`, and decide once whether you are
attributing by click date (`conversionsByClickDate`) — mixing the two across pulls produces
irreconcilable numbers.

## 4. Page

`limit` + `offset`, with `count` / `totalCount` in the response. There is no cursor. Page until
`offset + count >= totalCount`.

## 5. Respect the reporting limits

Reporting is metered separately from the rest of the API:

- **30 requests per minute per marketer** across the performance reporting API.
- **50 requests per minute per marketer** for the realtime reporting endpoints
  (`periodicHourly`, `periodicMinutely`, `sections/dateHourly`, `sections/dateMinutely`).
- **30 requests per second** for the token overall.

On `429`, sleep `rate-limit-msec-left` milliseconds. When backfilling many marketers, serialise per
marketer rather than fanning out — the limit is per marketer, and the token cap is global.
