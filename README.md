# Outbrain (outbrain)
Outbrain Inc. (NASDAQ: OB), which closed its acquisition of Teads in early 2025 and now operates publicly as Teads, is one of the largest open-internet advertising platforms — reaching 2 billion+ consumers per month across 50+ markets, with 20,000+ direct advertisers and 10,000+ premium media properties. The combined company spans open-web native (Outbrain Amplify), premium video, display, and Connected TV (Teads), powered by a Predictive AI engine and an omnichannel data graph.

**URL:** [Visit APIs.json](https://raw.githubusercontent.com/api-evangelist/outbrain/refs/heads/main/apis.yml)

**Run:** [Capabilities Using Naftiko](https://github.com/naftiko/fleet?utm_source=api-evangelist&utm_medium=readme&utm_campaign=company-api-evangelist&utm_content=repo)

## Tags

 - Advertising, Native Advertising, Open Web, CTV, Connected TV, Video Advertising, Content Discovery, Programmatic, Performance Marketing, AdTech, Teads

## Timestamps

- **Created:** 2026-05-25
- **Modified:** 2026-05-25

## Combined Company Snapshot

| Metric | Value |
|---|---|
| Ticker | NASDAQ: OB |
| Combined transaction value | ~$1B (closed Q1 2025) |
| Brand | Teads (post-merger consolidated brand) |
| Reach | 2B+ consumers / month |
| Markets | 50+ |
| Direct advertisers | 20,000+ |
| Premium media properties | 10,000+ |
| Ad opportunities | 18B / day |
| Engineering scale | 500+ microservices, 8M req/sec, 1B predictions/sec |
| Engineering hubs | Paris, Netanya, Montpellier, Ljubljana |
| HQ | New York, NY (US-managed) |

## APIs

### Outbrain Amplify API
The Outbrain Amplify API enables advertisers, agencies, and technology partners to integrate Amplify campaign management and reporting into their own platforms. Core resources are Marketer, Campaign, PromotedLink, Budget, AudienceTargeting, and a family of PerformanceBy* reporting endpoints.

**Human URL:** [https://developer.outbrain.com/home-page/amplify-api/](https://developer.outbrain.com/home-page/amplify-api/)

- [Documentation — Developer Center](https://developer.outbrain.com/home-page/amplify-api/)
- [Documentation — Reference](https://developer.outbrain.com/home-page/amplify-api/documentation/)
- [Documentation — Apiary](https://amplifyv01.docs.apiary.io/)
- [OpenAPI](openapi/outbrain-amplify-api-openapi.yml)
- [JSON Schema — Campaign](json-schema/outbrain-campaign-schema.json)
- [JSON Schema — Promoted Link](json-schema/outbrain-promoted-link-schema.json)
- [JSON Structure — Campaign](json-structure/outbrain-campaign-structure.json)
- [JSON-LD](json-ld/outbrain-context.jsonld)
- [Naftiko Capability — Marketers](capabilities/amplify-marketers.yaml)
- [Naftiko Capability — Campaigns](capabilities/amplify-campaigns.yaml)
- [Naftiko Capability — Promoted Links](capabilities/amplify-promoted-links.yaml)
- [Naftiko Capability — Budgets](capabilities/amplify-budgets.yaml)
- [Naftiko Capability — Targeting](capabilities/amplify-targeting.yaml)
- [Naftiko Capability — Reporting](capabilities/amplify-reporting.yaml)

### Outbrain Engage API
Publisher-facing content recommendation API. Returns mixed organic and paid (sponsored) recommendations for rendering in Outbrain widgets via the JS Widget, the iOS / Android Mobile SDK, Smartfeed, and mediation integrations across the open web.

**Human URL:** [https://developer.outbrain.com/apis/](https://developer.outbrain.com/apis/)

- [Documentation — APIs Overview](https://developer.outbrain.com/apis/)
- [Documentation — JS Widget Implementation](https://developer.outbrain.com/outbrain-javascript-implementation-guide/)
- [OpenAPI](openapi/outbrain-engage-api-openapi.yml)
- [JSON Schema — Recommendation](json-schema/outbrain-recommendation-schema.json)
- [Naftiko Capability — Recommendations](capabilities/engage-recommendations.yaml)

### Teads / Outbrain Conversion API
Server-to-server Conversion API for advertisers running on the combined Teads / Outbrain open-internet platform. Send first-party conversion events (Purchase, Lead, AddToCart, ViewContent) directly from backends or server-side GTM, independent of browser cookies.

**Human URL:** [https://www.teads.com](https://www.teads.com)

- [GTM Server Template (source)](https://github.com/teads/teads-advertiser-conversion-api-gtm-template)
- [OpenAPI](openapi/outbrain-teads-conversion-api-openapi.yml)
- [Naftiko Capability — Conversion API](capabilities/teads-conversion-api.yaml)

## Authentication

The Amplify API uses HTTP Basic at `/login` (rate limited to 2 req/hour/user) to issue an opaque token returned as `OB-TOKEN-V1`. All subsequent requests send this token in the `OB-TOKEN-V1` header.

```bash
curl -u "$OB_USER:$OB_PASS" https://api.outbrain.com/amplify/v0.1/login
# returns: { "OB-TOKEN-V1": "..." }
curl -H "OB-TOKEN-V1: $TOKEN" https://api.outbrain.com/amplify/v0.1/marketers
```

## Rate Limits

| Scope | Limit |
|---|---|
| `/login` (HTTP Basic) | 2 req / hour / user |
| Any single OB-TOKEN-V1 token | 30 req / second |
| Performance reporting per marketer | 10 req / minute |
| Real-time performance reporting per marketer | 50 req / minute |

Full machine-readable definition in [`rate-limits/outbrain-rate-limits.yml`](rate-limits/outbrain-rate-limits.yml).

## Plans, Rate Limits, FinOps

- [Plans — `plans/outbrain-plans-pricing.yml`](plans/outbrain-plans-pricing.yml)
- [Rate Limits — `rate-limits/outbrain-rate-limits.yml`](rate-limits/outbrain-rate-limits.yml)
- [FinOps — `finops/outbrain-finops.yml`](finops/outbrain-finops.yml)

## SDKs and Tools

- [Teads iOS SDK](https://github.com/teads/TeadsSDK-iOS)
- [Teads Android SDK](https://github.com/teads/TeadsSDK-android)
- [Teads React Native SDK](https://github.com/teads/TeadsSDK-ReactNative)
- [Teads GTM template](https://github.com/teads/teads-gtm-template)
- [Teads Conversion API GTM server-side template](https://github.com/teads/teads-advertiser-conversion-api-gtm-template)
- [Teads Prebid Server fork](https://github.com/teads/prebid-server-fork)
- [Outbrain Mobile SDK Docs](https://sdk.outbrain.com)
- [Outbrain JS Widget Implementation Guide](https://developer.outbrain.com/outbrain-javascript-implementation-guide/)
- [Outbrain go-secretcrypt](https://github.com/outbrain/go-secretcrypt)
- [Outbrain Elasticsearch Prometheus Exporter](https://github.com/outbrain/elasticsearch_exporter)

## Common

- [Outbrain](https://www.outbrain.com)
- [Teads](https://www.teads.com)
- [Outbrain Developer Center](https://developer.outbrain.com)
- [Teads Engineering](https://engineering.teads.com)
- [Teads Academy](https://academy.teads.com)
- [Partner API Access Request](https://www.outbrain.com/partner-api/)
- [Outbrain GitHub Org](https://github.com/outbrain)
- [Teads GitHub Org](https://github.com/teads)
- [Amplify API Google Group](https://groups.google.com/g/outbrain-amplifyapi)
- [Outbrain Help Center](https://www.outbrain.com/help/)
- [Legal](https://www.outbrain.com/legal/)
- [Privacy Policy](https://www.outbrain.com/privacy/)
- [Outbrain Blog](https://www.outbrain.com/blog/)
- [Teads Blog](https://www.teads.com/blog/)

## Maintainers

| Name | Contact |
|---|---|
| Kin Lane | [info@apievangelist.com](mailto:info@apievangelist.com) — [@apievangelist](https://twitter.com/apievangelist) — [apievangelist.com](https://apievangelist.com) |
