# ByKaranteli (bykaranteli)

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
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

A crypto-derivatives market-structure data service built on a deterministic crypto-futures signal engine. Its free, no-key public REST API surfaces funding rates/arbitrage, open interest, liquidation maps, options (Deribit), ETF flows, order-flow toxicity (VPIN), Coinbase premium, CFTC COT positioning, and Fear & Greed / BTC-dominance indices, plus live signal performance and per-symbol/strategy leaderboards. It also offers a hosted MCP server, x402 agent-payment endpoints, and CC0 datasets.

**APIs.json:** [https://bykaranteli.apievangelist.com/apis.yml](https://bykaranteli.apievangelist.com/apis.yml)

## Tags

- Cryptocurrency
- Crypto Derivatives
- Market Data
- Funding Rates
- Open Interest
- Liquidations
- Options
- ETF Flows
- Financial Data
- MCP
- x402
- Agents

## Timestamps

- **Created:** 2026-08-09
- **Modified:** 2026-08-09

## APIs

### ByKaranteli X402 API

Per-call priced history and depth endpoints, settled in USDC over the x402 protocol on Solana and Base mainnet through the Coinbase CDP facilitator. 13 priced endpoints plus the free catalog at /api/x402, which is the authoritative price list. Verified 2026-08-11: the catalog lists 13 endpoints from $0.002 to $0.010, and a priced endpoint returns HTTP 402. These sell depth and history, never access.

- **Human URL:** [https://bykaranteli.com/developers](https://bykaranteli.com/developers)
- **Base URL:** `https://bykaranteli.com`

#### Tags

- X402

#### Properties

- [OpenAPI](openapi/bykaranteli-x402-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/bykaranteli-x402-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/bykaranteli-x402-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Overlay](overlays/bykaranteli-x402-overlay.yaml)
- [Examples](examples/_index.yml)
- [Documentation](https://bykaranteli.com/developers)
- [L L Ms Txt](llms/bykaranteli-llms.txt)
- [Tool Crosswalk](mcp/bykaranteli-tool-crosswalk.yml)
- [A P I Catalog](well-known/bykaranteli-public-manifest.json)

### ByKaranteli Public API

The free, no-key public REST surface — 10 endpoints under /api/v1/public/ described by the provider's own self-describing manifest, plus the /api/public/ index endpoints. Verified 2026-08-11: unauthenticated, HTTP 200, `access-control-allow-origin: *`, 5-minute cache. NO OpenAPI is registered for this surface because the provider does not publish one — their openapi.json covers the x402 endpoints only. The manifest below is the machine-readable description that does exist; nothing here is reconstructed.

- **Human URL:** [https://bykaranteli.com/developers](https://bykaranteli.com/developers)
- **Base URL:** `https://bykaranteli.com`

#### Tags

- Market Data

#### Properties

- [Documentation](https://bykaranteli.com/developers)
- [A P I Catalog](well-known/bykaranteli-public-manifest.json)
- [Postman Collection](collections/bykaranteli-x402-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/bykaranteli-x402-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [M C P Server](mcp/bykaranteli-mcp.yml)
- [Documentation](https://bykaranteli.com/developers)
- [Agentic Access](agentic-access/bykaranteli-agentic-access.yml)
- [Domain Security](security/bykaranteli-domain-security.yml)
- [Developer Portal](https://bykaranteli.com/developers)
- [API Reference](https://bykaranteli.com/developers)
- [Getting Started](https://bykaranteli.com/guide)
- [Support](https://t.me/bykaranteli_com)
- [GitHub Organization](https://github.com/bykarantelicom)
- [Pricing](https://bykaranteli.com/pricing)
- [Sign Up](https://bykaranteli.com/register)
- [Login](https://bykaranteli.com/login)
- [Status Page](https://bykaranteli.com/status)
- [Changelog](changelog/bykaranteli-changelog.yml)
- [Lifecycle](lifecycle/bykaranteli-lifecycle.yml)
- [Authentication](authentication/bykaranteli-authentication.yml)
- [Conventions](conventions/bykaranteli-conventions.yml)
- [Error Catalog](errors/bykaranteli-problem-types.yml)
- [Rate Limits](rate-limits/bykaranteli-rate-limits.yml)
- [Plans](plans/bykaranteli-plans.yml)
- [Fin Ops](finops/bykaranteli-finops.yml)
- [Packages](packages/bykaranteli-packages.yml)
- [Conformance](conformance/bykaranteli-conformance.yml)
- [Vocabulary](vocabulary/bykaranteli-vocabulary.yml)
- [Components](components/bykaranteli-components.yml)
- [Agent Skill](skills/_index.yml)

## Maintainers

**FN:** ByKaranteli
**Email:** support@bykaranteli.com
**URL:** https://bykaranteli.com
