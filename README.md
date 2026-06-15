# Outbrain (outbrain)

Outbrain Inc. (NASDAQ&#58; OB), which closed its acquisition of Teads in early 2025 and now operates publicly as Teads, is one of the largest open-internet advertising platforms — reaching 2 billion+ consumers per month across 50+ markets, with 20,000+ direct advertisers and 10,000+ premium media properties. The combined company spans open-web native (Outbrain Amplify), premium video, display, and Connected TV (Teads), powered by a Predictive AI engine and an omnichannel data graph. Developer surface area centers on the Amplify API (campaign management + reporting), the Engage API (publisher content recommendations and the JS Widget / Mobile SDK), and a server-side Conversion API for cookieless measurement and optimization.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/outbrain/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/outbrain/refs/heads/main/apis.yml)

## Scope

- **Position:** Consuming
- **Access:** 3rd-Party

## Tags

- Advertising
- Native Advertising
- Open Web
- CTV
- Connected TV
- Video Advertising
- Content Discovery
- Programmatic
- Performance Marketing
- AdTech
- Teads

## Timestamps

- **Created:** 2026-05-25T00:00:00.000Z
- **Modified:** 2026-05-25

## APIs

### Outbrain Amplify API

The Outbrain Amplify API enables advertisers, agencies, and technology partners to integrate Amplify campaign management and reporting into their own platforms. Core resources are Marketer, Campaign, PromotedLink, Budget, AudienceTargeting, and a family of PerformanceBy* reporting endpoints. Authentication is HTTP Basic at /login (2 req/hour) returning an OB-TOKEN-V1 token (30 req/sec, 10 req/min for reporting, 50 req/min for realtime).

- **Human URL:** [https://developer.outbrain.com/home-page/amplify-api/](https://developer.outbrain.com/home-page/amplify-api/)

#### Tags

- Advertising
- Native Advertising
- Open Web
- Campaigns

#### Properties

- [Documentation](https://developer.outbrain.com/home-page/amplify-api/)
- [Documentation](https://developer.outbrain.com/home-page/amplify-api/documentation/)
- [Documentation](https://amplifyv01.docs.apiary.io/)
- [OpenAPI](openapi/outbrain-amplify-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/outbrain-amplify-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/outbrain-amplify-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [JSON Schema](json-schema/outbrain-campaign-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/outbrain-promoted-link-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Structure](json-structure/outbrain-campaign-structure.json)
- [JSON-LD](json-ld/outbrain-context.jsonld) — [JSON-LD](https://www.w3.org/TR/json-ld11/)

### Outbrain Engage API

Publisher-facing content recommendation API. Returns mixed organic and paid (sponsored) recommendations for rendering in Outbrain widgets via the JS Widget, the iOS/Android Mobile SDK, Smartfeed, and mediation integrations across the open web.

- **Human URL:** [https://developer.outbrain.com/apis/](https://developer.outbrain.com/apis/)

#### Tags

- Advertising
- Content Discovery
- Recommendations
- Open Web
- Publisher

#### Properties

- [Documentation](https://developer.outbrain.com/apis/)
- [Documentation](https://developer.outbrain.com/apis/engage-web-technologies/)
- [Documentation](https://developer.outbrain.com/outbrain-javascript-implementation-guide/)
- [OpenAPI](openapi/outbrain-engage-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/outbrain-engage-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/outbrain-engage-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [JSON Schema](json-schema/outbrain-recommendation-schema.json) — [JSON Schema](https://json-schema.org/specification)

### Teads / Outbrain Conversion API

Server-to-server Conversion API for advertisers running on the combined Teads / Outbrain open-internet platform. Lets advertisers send first-party conversion events (Purchase, Lead, AddToCart, ViewContent) directly from backends or server-side GTM, independent of browser cookies. Modeled on the public Teads server-side GTM template.

- **Human URL:** [https://www.teads.com](https://www.teads.com)

#### Tags

- Advertising
- Conversion API
- Server Side
- Measurement
- First Party Data

#### Properties

- [Documentation](https://www.teads.com)
- [Source Code](https://github.com/teads/teads-advertiser-conversion-api-gtm-template)
- [OpenAPI](openapi/outbrain-teads-conversion-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/outbrain-teads-conversion-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/outbrain-teads-conversion-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [Portal](https://www.outbrain.com)
- [Portal](https://www.teads.com)
- [Documentation](https://developer.outbrain.com)
- [Documentation](https://developer.outbrain.com/apis/)
- [Documentation](https://developer.outbrain.com/home-page/amplify-api/)
- [Documentation](https://developer.outbrain.com/home-page/amplify-api/documentation/)
- [Documentation](https://amplifyv01.docs.apiary.io/)
- [Documentation](https://teadsapi.docs.apiary.io/)
- [Sign Up](https://www.outbrain.com/partner-api/)
- [Sign Up](https://developer.outbrain.com/home-page/amplify-api/apply/)
- [Documentation](https://developer.outbrain.com/outbrain-javascript-implementation-guide/)
- [Documentation](https://developer.outbrain.com/apis/outbrain-js-api-guide/)
- [SDK](https://sdk.outbrain.com)
- [Documentation](https://www.outbrain.com/help/advertisers/amplify-api/)
- [Training](https://academy.teads.com)
- [Blog](https://engineering.teads.com)
- [Blog](https://blog.outbrain.com)
- [Blog](https://www.outbrain.com/blog/)
- [Blog](https://www.teads.com/blog/)
- [Documentation](https://investors.teads.com)
- [Terms of Service](https://www.outbrain.com/legal/)
- [Privacy Policy](https://www.outbrain.com/privacy/)
- [Support](https://www.outbrain.com/help/)
- [Forum](https://groups.google.com/g/outbrain-amplifyapi)
- [GitHub Organization](https://github.com/outbrain)
- [GitHub Organization](https://github.com/teads)
- [SDK](https://github.com/teads/TeadsSDK-iOS)
- [SDK](https://github.com/teads/TeadsSDK-android)
- [SDK](https://github.com/teads/TeadsSDK-ReactNative)
- [Tool](https://github.com/teads/teads-gtm-template)
- [Tool](https://github.com/teads/teads-advertiser-conversion-api-gtm-template)
- [Tool](https://github.com/teads/prebid-server-fork)
- [Tool](https://github.com/outbrain/go-secretcrypt)
- [Tool](https://github.com/outbrain/gracefulshutdown)
- [Tool](https://github.com/outbrain/elasticsearch_exporter)
- [LinkedIn](https://www.linkedin.com/company/teads)
- [LinkedIn](https://www.linkedin.com/company/outbrain)
- [Twitter](https://twitter.com/outbrain)
- [Twitter](https://twitter.com/teads)
- [Plans](plans/outbrain-plans-pricing.yml)
- [Rate Limits](rate-limits/outbrain-rate-limits.yml)
- [Fin Ops](finops/outbrain-finops.yml)
- [Vocabulary](vocabulary/outbrain-vocabulary.yml)
- [Spectral Rules](rules/outbrain-rules.yml)
- [Features](undefined)

## Maintainers

**FN:** Kin Lane
**Email:** info@apievangelist.com
**URL:** https://apievangelist.com
