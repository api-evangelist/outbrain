---
name: Fund, launch and creative-load an Outbrain Amplify campaign
description: Create a budget, create a campaign against it, attach promoted links, and enable the campaign — respecting Outbrain's minimum-budget enforcement and its lack of idempotency.
api: openapi/outbrain-amplify-api-full-openapi.yml
operations:
  - getMarketers
  - getCurrencies
  - createMarketersIdBudgets
  - createCampaigns
  - createCampaignsCampaignIdPromotedLinks
  - createCampaignsCampaignIdMultiplePromotedLinks
  - getCampaignsIdPromotedLinks
  - updateCampaignsId
---

# Launch an Outbrain Amplify campaign

Base URL: `https://api.outbrain.com/amplify/v0.1`. Authenticate first — see
`outbrain-authenticate-and-list-marketers`.

## 1. Resolve the marketer and its currency

`getMarketers` gives you the marketer id. `getCurrencies` (`GET /currencies`) returns the supported
currencies **and the per-currency budget minimums** — read it rather than assuming USD thresholds.

## 2. Create the budget

`createMarketersIdBudgets` (`POST /marketers/{id}/budgets`).

Minimums are enforced server-side and were raised on **2025-11-03**:

| `type` | minimum `amount` |
|---|---|
| `DAILY` | 25 USD |
| `MONTHLY` | 750 USD |
| `CAMPAIGN` | 25 USD x number of campaign days |

A budget below the minimum returns `400` with `{"moreInfo": ..., "errorMessage": ...}`. Other
currencies use the thresholds from `getCurrencies`.

Useful budget fields: `name`, `amount`, `type`, `pacing` (`AUTOMATIC` / `SPEND_ASAP`), `startDate`,
`runForever`, `shared`. A shared budget can fund several campaigns.

## 3. Create the campaign

`createCampaigns` (`POST /campaigns`) referencing the `budgetId` you just created. Set `cpc`,
targeting and, if you are using Conversion Bid Strategy, the goal configuration.

Create the campaign **disabled**, load creatives, then enable it with `updateCampaignsId`
(`PUT /campaigns/{id}`). That ordering avoids serving an empty campaign.

## 4. Attach promoted links

One creative: `createCampaignsCampaignIdPromotedLinks`
(`POST /campaigns/{campaignId}/promotedLinks`).

Several at once: `createCampaignsCampaignIdMultiplePromotedLinks`
(`POST /campaigns/{campaignId}/multiplePromotedLinks`). **Prefer the bulk operation.** This API has
no idempotency key, so a partial failure across N single POSTs leaves you reconciling by hand.

Per-ad brand logos are read and written through `logoMetadata`, exposed on a PromotedLink read with
`extraFields=LogoMetaData` (added 2026-08-13).

## 5. Verify before you enable

Call `getCampaignsIdPromotedLinks` (`GET /campaigns/{id}/promotedLinks`) and confirm the creative
count matches what you sent. Because there is no idempotency key, this read is the only way to tell
a retried create from a duplicate. Then flip `enabled` with `updateCampaignsId`.

## Failure handling

- `400` — usually the budget minimum or a missing `Content-Type: application/json`.
- `403` — the token is valid but not permitted on that marketer. Re-check `getMarketers`.
- `429` — sleep `rate-limit-msec-left` milliseconds, then continue. Do not retry immediately.
