# ByKaranteli

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

**Areas:** Cryptocurrency · Crypto Derivatives · Market Data · Funding Rates · Open Interest · Liquidations · Options · ETF Flows · Financial Data · MCP · x402 · Agents

## ByKaranteli on APIs.io

Everything profiled for ByKaranteli is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/bykaranteli/](https://apis.io/providers/bykaranteli/)** — or go straight to one of the APIs or properties below.

### APIs (2)

- [ByKaranteli X402 API](https://apis.io/apis/bykaranteli/bykaranteli-x402-api/) — Per-call priced history and depth endpoints, settled in USDC over the x402 protocol on Solana and Base mainnet through the Coinbase CDP facilitator. 13…
- [ByKaranteli Public API](https://apis.io/apis/bykaranteli/bykaranteli-public-api/) — The free, no-key public REST surface — 10 endpoints under /api/v1/public/ described by the provider's own self-describing manifest, plus the /api/public/…

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [bykaranteli](https://apis.io/servers/bykaranteli/bykaranteli/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Bykaranteli Agentic Access](https://apis.io/agentic-access/bykaranteli/bykaranteli-agentic-access/)

#### Vocabulary (1)

The provider's domain terms, defined.

- [ByKaranteli crypto derivatives glossary Vocabulary](https://apis.io/vocabularies/bykaranteli/bykaranteli-vocabulary/)

#### Examples (6)

Example requests and responses.

- [Bykaranteli Public Indices](https://apis.io/examples/bykaranteli/bykaranteli-public-indices/)
- [Bykaranteli Public Pressure](https://apis.io/examples/bykaranteli/bykaranteli-public-pressure/)
- [Bykaranteli Public Recent](https://apis.io/examples/bykaranteli/bykaranteli-public-recent/)
- [Bykaranteli V1 Health](https://apis.io/examples/bykaranteli/bykaranteli-v1-health/)
- [Bykaranteli V1 Leaderboard](https://apis.io/examples/bykaranteli/bykaranteli-v1-leaderboard/)
- [Bykaranteli X402 Payment Required](https://apis.io/examples/bykaranteli/bykaranteli-x402-payment-required/)

#### Collections (1)

Postman and Open Collection request collections.

- [ByKaranteli crypto derivatives data X402 API](https://apis.io/collections/bykaranteli/open-bykaranteli-x402-api/)

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [Bykaranteli X402 Overlay](https://apis.io/overlays/bykaranteli/bykaranteli-x402-overlay/)

#### Governance rules (1)

Spectral rulesets for the provider's contracts.

- [Moved to /providers/bykaranteli/](https://apis.io/rules/bykaranteli/bykaranteli-rules/)

#### Security (3)

Authentication, trust centre, and vulnerability disclosure.

- [Bykaranteli Authentication](https://apis.io/security/bykaranteli/bykaranteli-authentication/)
- [Bykaranteli Domain Security](https://apis.io/security/bykaranteli/bykaranteli-domain-security/)
- [Bykaranteli Vulnerability Disclosure](https://apis.io/security/bykaranteli/bykaranteli-vulnerability-disclosure/)

#### Plans and pricing (2)

Published plans, tiers and prices.

- [Bykaranteli Plans](https://apis.io/plans/bykaranteli/bykaranteli-plans/)
- [Bykaranteli Plans Pricing](https://apis.io/plans/bykaranteli/bykaranteli-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Bykaranteli Rate Limits](https://apis.io/rate-limits/bykaranteli/bykaranteli-rate-limits/)

#### FinOps (1)

What the API costs to run, by operation.

- [Bykaranteli Finops](https://apis.io/finops/bykaranteli/bykaranteli-finops/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.bykaranteli.com/)
- [Documentation](https://bykaranteli.com/developers)
- [Getting started](https://bykaranteli.com/guide)
- [API reference](https://bykaranteli.com/developers)
- [Pricing](https://bykaranteli.com/pricing)
- [Sign up](https://bykaranteli.com/register)
- [Support](https://t.me/bykaranteli_com)
- [Security](https://bykaranteli.com/security)
- [Terms of service](https://bykaranteli.com/terms)
- [Privacy policy](https://bykaranteli.com/privacy)
- [GitHub](https://github.com/bykarantelicom)
- [Status](https://bykaranteli.com/status)

## API Evangelist rating

**Kin Score 61.1** — strong · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 68.3 |
| Contract quality | 46.8 |
| Contract governance | 33.3 |
| Operational transparency | 65.8 |
| Developer ergonomics | 63.7 |
| Access clarity | 76.3 |

**Agent readiness 39.4** — agent-ready (gated down from agent-native)

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | na |
| MCP Server | verified |
| Auth Clarity | bearer (partial credit) |
| Idempotency | na |
| Error Semantics | derived (partial credit) |
| OpenAPI Examples | documented (partial credit) |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | — |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | flavored (partial credit) |
| Dry Run Mode | na |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | na |
| Operation Distinctiveness | distinct |

**Regulatory alignment 34.3** — Securities & Market Data

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/bykaranteli/](https://apis.io/providers/bykaranteli/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for ByKaranteli: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/bykaranteli/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
