---
name: bykaranteli-liquidation-forensics
description: Reconstruct a crypto liquidation cascade — where the leverage clusters sat, what actually got force-liquidated, and in what order — using ByKaranteli's free liquidation surface and its paid raw event tape.
generated: '2026-08-09'
method: generated
source: mcp/bykaranteli-mcp-tools.json + openapi/bykaranteli-x402-openapi.json
api: ByKaranteli
surfaces:
  mcp: https://mcp.bykaranteli.com
  openapi: https://bykaranteli.com/openapi.json
tools:
  - get_liquidations
  - get_liquidation_cascades
  - get_open_interest
  - get_flow_toxicity
operations:
  - liqmap-levels
  - liquidations-raw
  - spot-microstructure
cost: 'free through step 3; $0.005 liqmap-levels, $0.010 liquidations-raw, $0.010 spot-microstructure'
---

# Liquidation cascade forensics

A cascade is a feedback loop: forced sells hit thin liquidity, price gaps to the
next leverage cluster, that cluster liquidates. To reconstruct one you need
three things — where the clusters were, what actually liquidated, and how toxic
the flow was while it happened. ByKaranteli gives you the first cheaply and the
last two for cents.

## 1. Establish the day and the scale — free

Call the MCP tool `get_liquidations` with `symbol` (uppercase, pattern
`^[A-Z0-9]{2,20}$`) and `days` (1-90). It returns daily long and short
liquidation totals in USD per symbol and exchange, recorded from ByKaranteli's
own Binance, Bybit and OKX socket collectors.

Two things matter about this series: it is **recorded events, a floor, not an
estimate**, and its **history begins 2026-07-30**. Do not ask it about an older
cascade — it does not have one.

## 2. Get the cascade shape — free

Call `get_liquidation_cascades`. It returns clustered liquidation events and
their sequence. Use it to identify the candidate cascade window; use
`get_open_interest` to confirm OI actually fell through that window rather than
rotating.

## 3. Read the toxicity — free

Call `get_flow_toxicity` for the live VPIN read on BTC, ETH and SOL. High VPIN
during the window is the signature of informed/one-sided flow rather than a
liquidity air pocket.

## 4. Buy the map — x402, $0.005

Call the paid operation `liqmap-levels`
(`GET https://bykaranteli.com/api/x402/liqmap-levels`). It returns the full
multi-exchange liquidation map snapshot for a Binance USDT-M perp: modeled
leverage clusters, **real forceOrder levels**, top magnets, funding, OI and
orderbook context.

The free preview at `GET https://bykaranteli.com/api/liqmap/public?symbol=BTC`
is available first — check whether the preview already answers your question
before spending.

## 5. Buy the tape — x402, $0.010

Call `liquidations-raw`
(`GET https://bykaranteli.com/api/x402/liquidations-raw`) for individual
liquidation events with side, price, quantity, notional, venue and millisecond
timestamp across Binance, Bybit and OKX. This is the only surface that gives you
ordering — the free tool aggregates to daily totals and loses the sequence.

If you need the liquidity side of the loop, add `spot-microstructure` ($0.010):
minute bars with the taker-buy versus total quote-volume split, pre-joined
across venues and retained past exchange limits.

## Paying

Every `/api/x402/*` call answers `402` first, with x402 v2 payment requirements
in a base64 `payment-required` header — `accepts[]` carrying network
(`solana:...` or `eip155:8453`), USDC amount, `payTo` and a 300s
`maxTimeoutSeconds`, plus a `bazaar` extension whose JSON Schema describes the
call's input and output. An x402 client settles and retries automatically.
**Only a successful response settles; a failure costs nothing.** There is no
account, no key and no minimum.

Check the free catalog at `GET https://bykaranteli.com/api/x402` (operationId
`x402Catalog`) for current prices before budgeting a run — it is free and
authoritative.

## Conventions that apply

- **Auth:** none anywhere in this flow. The paid calls authenticate the payment,
  not an identity.
- **Errors:** `{ "error": "<code>", "message": "<human>" }`, `application/json`,
  not RFC 9457. The only error the paid surface documents is `402`.
- **Rate limits:** docs say 20 req/min/IP, the manifest says no public per-IP
  limit. No `RateLimit-*` headers are emitted. Back off on `429` +
  `Retry-After`.
- **Attribution:** commercial use is allowed; a visible link back to
  bykaranteli.com is requested when you republish the numbers, and rebranding
  them as your own in-house research is explicitly not allowed.
