---
name: bykaranteli-x402-pay-per-call
description: Buy a single ByKaranteli data answer as an autonomous agent — discover the catalog, read the 402 payment challenge, settle USDC on Solana or Base, and retry — with no account, no API key and no subscription.
generated: '2026-08-09'
method: generated
source: openapi/bykaranteli-x402-openapi.json + examples/bykaranteli-x402-payment-required.json
api: ByKaranteli
surfaces:
  openapi: https://bykaranteli.com/openapi.json
  catalog: https://bykaranteli.com/api/x402
operations:
  - x402Catalog
  - flow-vpin
  - dvol-history
  - slippage-history
  - listings-history
  - funding-history
  - oi-history
  - cot-history
  - premium-history
  - options-flow
  - options-oi-history
  - liqmap-levels
  - liquidations-raw
  - spot-microstructure
cost: 'catalog free; priced operations $0.002-$0.010 per successful response'
---

# Paying ByKaranteli per call with x402

This is the whole point of the surface: an agent that needs one number can buy
exactly that number, without a signup flow, a credit card, an API key, or a
human in the loop. Read this before you spend anything.

## 1. Read the catalog first — it is free

`GET https://bykaranteli.com/api/x402` (operationId `x402Catalog`). It carries
`security: []` in the OpenAPI, meaning explicitly no payment. You get:

- `networks[]` — the accepted settlement rails and their `pay_to` addresses
- `endpoints[]` — every priced endpoint with `url`, `price_usd` and description

Never hardcode a price. Prices live in three authoritative places and the
catalog is the cheapest one to read.

## 2. Pick the cheapest operation that answers the question

| Price | Operations |
|---|---|
| $0.002 | `flow-vpin`, `dvol-history`, `slippage-history`, `listings-history` |
| $0.005 | `liqmap-levels`, `options-flow`, `premium-history`, `cot-history`, `oi-history`, `funding-history`, `options-oi-history` |
| $0.010 | `liquidations-raw`, `spot-microstructure` |

Before spending, check whether the **free** surface already answers it. Every
live snapshot on this platform is free and unmetered — the paid tier sells
*depth and history*, never access. The hosted MCP server at
`https://mcp.bykaranteli.com` exposes 20 free read-only tools covering the live
view of most of these same domains (see `mcp/bykaranteli-tool-crosswalk.yml`).

## 3. Call without payment and read the challenge

```
GET https://bykaranteli.com/api/x402/flow-vpin
-> HTTP 402
   payment-required: <base64>
   body: {}
```

Base64-decode the `payment-required` header. It is an x402 **v2** document:

- `resource` — `url`, `description`, `serviceName`, `tags`
- `accepts[]` — one entry per rail, each with `scheme: exact`, `network`,
  `amount` (in the asset's smallest unit — `"2000"` is $0.002 of 6-decimal
  USDC), `asset`, `payTo`, and `maxTimeoutSeconds: 300`
- `extensions.bazaar` — an `info` block describing the HTTP input and a JSON
  example of the output, plus a JSON-Schema-2020-12 `schema` for both

The two rails currently offered are Solana mainnet
(`solana:5eykt4UsFv8P8NJdTREpY1vzqKqZKvdp`, USDC mint
`EPjFWdd5AufqSSqeM2qN1xzybapC8G4wEGGkZwyTDt1v`) and Base mainnet
(`eip155:8453`, USDC contract `0x833589fCD6eDb6E08f4c7C32D4f71b54bdA02913`).
Network fees are covered by the facilitator. A verbatim decoded challenge is
saved at `examples/bykaranteli-x402-payment-required.json`.

## 4. Settle and retry

```
npm i @x402/fetch @x402/core @x402/svm
// wrapFetchWithPayment(fetch, client) -> 200 + data, settled in USDC
```

The wrapped fetch reads the challenge, settles, attaches `X-PAYMENT` and
retries inside the 300-second window. You do not implement the protocol.

## 5. Budgeting rules that actually hold here

- **You are billed per successful response.** A failed request settles nothing.
  A retry after a failure is not a double charge.
- **No minimum, no prepay, no invoice.** There is nothing to reconcile monthly.
- **Set a per-run cap anyway.** A loop over 500 symbols at `liquidations-raw`
  ($0.010) is $5.00, and nothing in the protocol stops it. Treat every
  `/api/x402/*` call as `consequence: spend` and require explicit approval —
  that is exactly how `overlays/bykaranteli-x402-overlay.yaml` classifies them.
- **The response schema is in the challenge, not the spec.** The published
  OpenAPI declares no `components.schemas`; the `bazaar` extension in the 402 is
  where the shape lives. Parse it from there.

## 6. What you cannot do

There is no write surface. Every operation is `GET`, every tool is annotated
`readOnlyHint: true`, and the provider states no trading actions and no PII are
exposed. Payment is the only state-changing act in the entire estate.
