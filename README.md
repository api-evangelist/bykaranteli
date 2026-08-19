# ByKaranteli (bykaranteli)

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
