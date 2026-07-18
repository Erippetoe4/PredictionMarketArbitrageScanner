# Cross-Platform Prediction Market Arbitrage Scanner

A Python-based scanner that detects fee-adjusted mispricing between Kalshi and Polymarket on the same underlying event, and stress-tests flagged opportunities with a Monte Carlo execution-slippage simulation.

## What It Does

- Pulls active markets live from **Polymarket's Gamma API** and **Kalshi's REST API** (with an automatic synthetic-data fallback if either is unreachable)
- **Fuzzy-matches** equivalent events across platforms despite different question phrasing
- Detects **fee-adjusted arbitrage edge**: buying YES on the cheaper platform and NO on the more expensive one locks in a fixed $1 payout regardless of outcome
- Runs a **Monte Carlo simulation** of execution slippage to separate paper edge from realistically tradeable edge
- Auto-generates a **scan report** ranking actionable opportunities with explicit execution-risk flags

## How to Run

1. Open `Prediction_Market_Arbitrage_Scanner.ipynb` in Google Colab
2. Run all cells (`Runtime → Run all`)
3. Edit `CONFIG` in Section 1 to adjust fee assumptions, matching threshold, or position size
4. Re-run — the entire pipeline (data → matching → arbitrage detection → Monte Carlo → report) regenerates end to end

No API keys required. Both platforms' market-data endpoints are free and keyless for this use case.

## Tech Stack

`pandas` · `numpy` · `matplotlib` · `requests` · `difflib`

## Project Structure

```
├── Prediction_Market_Arbitrage_Scanner.ipynb   # main notebook
├── requirements.txt
└── README.md
```

## Disclaimer

Built for educational/portfolio purposes. Fee assumptions are simplified estimates, not official platform fee schedules. This is not a live-execution trading system, and nothing here constitutes financial advice.
