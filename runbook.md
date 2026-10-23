# AAPL Covered-Call Overlay Note

**Week of:** Friday, October 23, 2026
**Underlying:** Apple Inc. (AAPL) — Nasdaq (NMS)
**Data source:** Yahoo Finance quotes (equity quote + Nov 20, 2026 call chain, pulled 2026-10-23). The chain output was truncated by the pull tool, so the three near-the-money contracts were retrieved individually from the same Yahoo quote source; values below are as returned.

## Market snapshot

| Item | Value |
|---|---|
| **Current share price** | **$348.22** |
| Previous close | $343.99 |
| Day range | $342.28 – $348.36 |
| 52-week range | $243.42 – $348.36 |
| Volume / 10-day avg | 46,845,411 / 40,529,770 |
| Market cap | ≈ $5.08T |

**Expiration selected: Friday, November 20, 2026** — the nearest *standard monthly* (third-Friday) expiration in AAPL's listed expiration dates. Note: 2026-10-23 is the fourth Friday of October, and October's third-Friday monthly (Oct 16) has already passed, so the Nov 20 monthly is the next standard expiry.

## Three call strikes closest to the money (Nov 20, 2026)

Ordered by distance from the $348.22 spot. Values exactly as returned by the data source:

| Strike | Last price | Open interest | Distance from spot |
|---|---|---|---|
| **350** | $10.32 | 0 | 1.78 |
| **345** | $13.1 | 0 | 3.22 |
| **355** | $7.88 | 0 | 6.78 |

*Data-quality flag:* open interest came back as 0 for all three strikes in this pull. A cross-check of the same Nov 20 chain via Nasdaq's option-chain API returned non-zero open interest at lower strikes, so Yahoo's OI field may be unreliable this morning — treat the 0s with caution and re-verify before sizing.

**Overlay takeaway:** the 350 call is the closest to the money; at $10.32 against a $348.22 spot that is ≈2.96% premium for ~28 days, with $1.78 of upside before assignment. The 345 call ($13.1) is in-the-money by $3.22; the 355 call ($7.88) adds a $6.78 cushion but only ≈2.26% premium.

## Logging (Weights & Biases)

**Support bot:** could not be reached this week. We asked the W&B support bot three times (varying phrasings) how to log our daily-rebalanced backtest — runs, metrics, and time series. Every attempt returned an error rather than guidance, verbatim:

> `Error connecting to support bot: 404 Client Error: Not Found for url: https://morg--wandbot-api-wandbotapi-serve.modal.run/status`

No bot guidance was returned, so none is recorded here. Retry before relying on the bot for backtest-logging decisions this cycle.

**Official documentation (fetched live today):** from the Weights & Biases documentation page **"Runs"** (`docs.wandb.ai/products/wandb/runs.md`), which states:

> "Weights & Biases logs your run to a project. You specify the project when you initialize the run with `wandb.init(project="")`."

— i.e., each backtest run should be initialized with `wandb.init(project=...)` so it lands in the intended project. (Documentation site now served under the CoreWeave docs umbrella; the page above is the W&B Runs page.)
