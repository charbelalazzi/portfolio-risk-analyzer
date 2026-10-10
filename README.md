# Portfolio Risk Analyzer

## Overview

A Python tool that pulls market data for a multi-asset portfolio and computes core risk and performance metrics —  annualised return, volatility, Sharpe ratio, and maximum drawdown — with supporting visualisations.

## Metrics Computed

- **Annualised return** — the portfolio’s weighted-average return, annualised over 252 trading days.
- **Annualised volatility** — the standard deviation of returns (scaled by √252), a measure of how much returns fluctuate: the standard proxy for risk.
- **Sharpe ratio** — return earned per unit of risk (risk-free rate assumed 0 for this version).
- **Maximum drawdown** — the largest peak-to-trough fall, i.e. the worst loss an investor would have endured.


## Key Findings

- The portfolio shows meaningful concentration — four holdings (QQQ, VTI, QTUM, MU) are highly correlated US-tech exposure (up to 0.95), so effective diversification comes mainly from NOK (Nokia) and the GBP-denominated CSP1.L.
- Over Oct 2023–Oct 2025 it returned ~36% annualised at ~20% volatility (Sharpe ~1.8), with a maximum drawdown of −21%.


## Visualisations

- Cumulative return growth and drawdown chart.
- Correlation heatmap.

## Limitations

- Risk free rate was assumed to 0%, which led to higher than expected sharpe ratio.
- No FX conversion — returns were computed in each asset’s local currency (five USD-listed, one GBP-listed) rather than converted to a single base currency.
- Short time window (two years) — a favourable period for tech that likely flatters returns; not representative of long-run performance.
- DRAM was initially a holding in the portfolio, but since the ETF was created in 2026, MU stock was used as a Proxy.

## Next Steps

- Incorporate a realistic risk-free rate into the Sharpe calculation.
- Introduce FX Conversion.
- Include rolling volatility. 
- Running the analysis on a longer time window.


## Tech Stack

Python · pandas · numpy · yfinance · matplotlib · seaborn

## How to Run

1. Clone the repo
2. `conda create -n portfolio python=3.12 && conda activate portfolio`
3. `conda install pandas numpy matplotlib seaborn ipykernel -y && pip install yfinance`
4. Open `analyzer.ipynb` and run all cells