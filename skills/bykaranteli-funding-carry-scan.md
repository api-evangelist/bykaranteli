---
name: bykaranteli-funding-carry-scan
description: Find and size a crypto funding-rate carry trade using ByKaranteli's free live funding data, then buy the settled funding history you need to check whether the spread persists.
generated: '2026-08-09'
method: generated
source: mcp/bykaranteli-mcp-tools.json + openapi/bykaranteli-x402-openapi.json
api: ByKaranteli
surfaces:
  mcp: https://mcp.bykaranteli.com
  openapi: https://bykaranteli.com/openapi.json
tools:
  - get_funding_arbitrage
  - get_funding_heatmap
  - get_pressure_scores
  - get_open_interest
operations:
  - funding-history
  - oi-history
cost: 'free until step 4; $0.005 per funding-history call, $0.005 per oi-history call'
---

# Funding carry scan

Funding-rate carry means holding a perp position on the venue that pays and the
offsetting leg on the venue that charges. The whole trade lives or dies on
whether today's spread is a persistent regime or a one-print artifact. This skill
uses the free surface to find candidates and the paid surface only to answer the
persistence question.

## 1. Get the current cross-exchange spread — free

Call the MCP tool `get_funding_arbitrage`. It takes no parameters and returns
current funding spreads across Binance, OKX, Bybit, Gate.io, HTX and BingX with a
net-of-cost annualized APR per pair. The equivalent free REST call is
`GET https://bykaranteli.com/api/public/funding-arb`.

Rank by net APR, not gross. The provider states the APR is already net of cost.

## 2. Confirm the funding side on the flagship venue — free

Call `get_funding_heatmap` with `symbol` set to the candidate ticker (uppercase,
e.g. `BTCUSDT`). It returns that symbol's funding rate per settlement interval,
its 24h open-interest change and its 24h price change across the top-30 Binance
USDT-M perps. Positive funding means longs pay shorts.

Reject any candidate where the funding sign disagrees with the arbitrage row —
that means the spread has already moved.

## 3. Check the positioning behind the spread — free

Call `get_pressure_scores` with `symbol` (and `limit` if you want a ranked
board). It returns a composite 0-100 derivatives pressure score built from OI
deltas, funding and basis, with a direction-aware regime label.

A wide funding spread on a symbol whose OI is collapsing is a spread that is
about to close. Treat a `*_RAMP` regime with rising OI as the persistent case.

## 4. Buy the history that settles the question — x402, $0.005

Only now spend. Call the paid operation `funding-history`
(`GET https://bykaranteli.com/api/x402/funding-history`) for settled funding
rate history per symbol and venue — the series behind carry and basis work.

The endpoint answers `402` with a base64 `payment-required` header carrying x402
v2 requirements: `accepts[]` with network, USDC amount, `payTo` and a 300-second
`maxTimeoutSeconds`. Any x402 client
(`wrapFetchWithPayment(fetch, client)` from `@x402/fetch` + `@x402/core` +
`@x402/svm`) pays and retries automatically. **Price is per successful
response — a failed request settles nothing.**

If you also need to see whether open interest supported the spread historically,
call `oi-history` (also $0.005) for five-minute normalised OI history.

## 5. Size it

Nothing on this API sizes a position for you and nothing here is investment
advice — the provider says so on every page. ByKaranteli publishes a Kelly-based
position sizer and a risk guide as human tools; there is no API for them.

## Conventions that apply

- **Auth:** none on steps 1-3. Steps 4-5 authenticate the *call*, not the caller
  — there is no account and no API key on the x402 surface.
- **Rate limits:** the docs say 20 req/min/IP; the machine-readable manifest says
  public endpoints have no per-IP limit. They disagree. Assume the stricter
  number and back off on `429` + `Retry-After`. No `RateLimit-*` headers are
  returned, so you cannot see your remaining budget.
- **Caching:** responses carry `Cache-Control: public, max-age=N, s-maxage=N`.
  Polling faster than the TTL buys you nothing.
- **Errors:** `{ "error": "<code>", "message": "<human>" }` as
  `application/json`. Not RFC 9457. The documented `ok: false` field is not
  always present — branch on `error`, not on `ok`.
- **Parameter ranges are clamped, not rejected.** An out-of-range `window` comes
  back silently truncated with a `200`. Read the window actually used out of the
  response body.
