---
name: Authenticate to the Outbrain Amplify API and list marketers
description: Obtain a 30-day OB-TOKEN-V1 token, cache it correctly against the 2-per-hour /login limit, and enumerate the marketer accounts the token can act on.
api: openapi/outbrain-amplify-api-full-openapi.yml
operations:
  - getLogin
  - getMarketers
  - getMarketersId
---

# Authenticate to the Outbrain Amplify API

Base URL: `https://api.outbrain.com/amplify/v0.1`

## 1. Get a token — but cache it

Call `getLogin` (`GET /login`) with HTTP Basic credentials. The response carries an opaque token.
Send it on every subsequent request in the **`OB-TOKEN-V1`** header. Do not send Basic credentials
anywhere else.

**The hard constraint:** `/login` is capped at **2 requests per hour per user**. An agent that
authenticates per-call will lock itself out within minutes. Store one token and reuse it.

- Tokens are valid for **30 days**. Refresh on a schedule shorter than that, not on 401.
- Generating a new token does **not** invalidate older ones, so refresh is safe to overlap.
- Changing the account password or email revokes **every** token issued before the change.
- A human can also mint a token from `https://my.outbrain.com/create-token`, which does not consume
  a `/login` call.

## 2. Find the accounts you can act on

Call `getMarketers` (`GET /marketers`) to list every marketer the token is permitted to reach.
Every other write in this API is scoped by a marketer id, so resolve this first and hold onto it.

For a single account use `getMarketersId` (`GET /marketers/{id}`). Pass `extraFields=Account` when
you need the **primary account id** — that is the identifier the account-level performance report
(`GET /reports/accounts/{primaryAccountId}/marketers`) requires, and it is not returned by default.

## 3. Rules that apply to every call after this

- `Content-Type: application/json` is required on every POST/PUT that carries an entity.
- A single token is limited to **30 requests per second** across the whole API.
- On any error the body is `{"moreInfo": "...", "errorMessage": "..."}` — not RFC 9457.
- On `429`, read the **`rate-limit-msec-left`** response header and sleep that many milliseconds.
  Every request inside that window will also 429.
- Every response carries an **`AMPLIFY-REQUEST-ID`** UUID. Log it. Outbrain support asks for it.
- There is **no idempotency key** on this API. A retried POST creates a second object. Verify with a
  read before retrying a write.
