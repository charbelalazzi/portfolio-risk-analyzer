# Portfolio Risk Analyzer

## Overview

A Python tool that pulls market data for a multi-asset portfolio and computes core risk and performance metrics —  annualised return, volatility, Sharpe ratio, and maximum drawdown — with supporting visualisations.

## Metrics Computed

- **Annualised return** — the portfolio’s weighted-average return, annualised over 252 trading days.
- **Annualised volatility** — the standard deviation of returns (scaled by √252), a measure of how much returns fluctuate: the standard proxy for risk.
- **Sharpe ratio** — return earned per unit of risk.
- **Maximum drawdown** — the largest peak-to-trough fall, i.e. the worst loss an investor would have endured.
- **VaR** - The loss that won’t be exceeded on X% of days.
- **Conditional VaR** - Average severity of a loss if the VaR threshold is breached.
- **Parametric VaR** - VaR computed using the normal distribution assumption.
- **Modified VaR** - VaR computed using the Cornish-Fisher expansion.


## Key Findings

- The portfolio shows meaningful concentration — four holdings (QQQ, VTI, QTUM, MU) are highly correlated US-tech exposure (up to 0.95), so effective diversification comes mainly from NOK (Nokia) and the GBP-denominated CSP1.L.
- Over Oct 2023–Oct 2026 it returned ~37% annualised at ~21% volatility (Sharpe ~1.55), with a maximum drawdown of −21%.
- VTI & CSP1.L show low level correlation based on the heatmap, although they replicate the same index. This can be explained by non-synchronous-trading correlation, since these two ETFs trade on different Exchanges and so have different Closing time and Holidays.  
- Difference between the VaR & CVaR is ~ 0.8%, suggesting wide tail risk, which is expected from a tech heavy portfolio.
- Parametric VaR is less severe than the historical VaR and the gap increases with confidence level, which can be explained by the Normal distribution assumption.
- The Cornish-Fisher √3 sign-flip: at 95% the Modified VaR is less severe than Parametric, but at 99% it flips sharply to far more severe
- Significant difference between Modified VaR and Parametric VaR at 99% Confidence level, which illustrats the limitations of using a Normal Distribution assumption.


## Visualisations

- Cumulative return growth and drawdown chart.
- Correlation heatmap.

## Limitations

- Short time window (three years) — a favourable period for tech that likely flatters returns; not representative of long-run performance.
- DRAM was initially a holding in the portfolio, but since the ETF was created in 2026, MU stock was used as a Proxy.

## Tech Stack

Python · pandas · numpy · yfinance · matplotlib · seaborn · empyrical · scipy

## How to Run

1. Clone the repo
2. `conda create -n portfolio python=3.12 && conda activate portfolio`
3. `conda install pandas numpy matplotlib seaborn ipykernel -y && pip install yfinance`
4. Open `Portfolio_Analyzer.ipynb` and run all cells