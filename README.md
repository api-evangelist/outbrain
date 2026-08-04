# Outbrain (outbrain)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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
