
 ⚡ Project  — Electricity Trading Risk Engine: VaR, CVaR and Monte Carlo Simulation

## Overview

This project develops a quantitative risk management framework for electricity trading markets.

The objective is to estimate downside risk exposure in the German electricity market using:

- Historical Value-at-Risk (VaR)
- Conditional Value-at-Risk (CVaR)
- Parametric Gaussian VaR
- Monte Carlo simulation
- Stress testing analysis

The project demonstrates how traditional financial risk management techniques can be adapted to electricity markets characterized by:

- Price spikes
- Heavy tails
- Extreme events
- Non-normal return distributions

---

## Dataset

Source:

- ENTSO-E Transparency Platform
- Open Power System Data

Market:

- Germany/Luxembourg (DE-LU)

Period:

- October 2018 – September 2020

Frequency:

- Hourly observations

---

## Methodology

### Return Construction

Because electricity prices can become negative, returns were computed using absolute price differences:

```text
r_t = P_t - P_{t-1}
```

---

## Distribution Analysis

### Descriptive Statistics

| Statistic | Value |
|---|---|
| Mean | -0.001 |
| Standard Deviation | 5.551 |
| Minimum | -101.91 |
| Maximum | 109.23 |
| Skewness | 0.486 |
| Kurtosis | 26.212 |

Findings:

- Strong positive skewness
- Extremely heavy tails
- Presence of extreme market events

---

## Historical Value-at-Risk

| Measure | Value |
|---|---|
| Historical VaR (95%) | -7.46 |
| Historical VaR (99%) | -14.22 |

---

## Conditional Value-at-Risk

| Measure | Value |
|---|---|
| Historical CVaR (95%) | -12.04 |
| Historical CVaR (99%) | -21.02 |

Findings:

Expected losses beyond the VaR threshold are substantially larger than the corresponding VaR estimates.

---

## Parametric Gaussian VaR

| Measure | Value |
|---|---|
| Gaussian VaR (95%) | -9.13 |
| Gaussian VaR (99%) | -12.91 |

Findings:

Gaussian assumptions underestimate extreme downside risk.

---

## Monte Carlo Risk Simulation

10,000 Monte Carlo scenarios were simulated assuming normally distributed returns.

### Results

| Measure | Value |
|---|---|
| Monte Carlo VaR (95%) | -9.17 |
| Monte Carlo VaR (99%) | -13.13 |
| Monte Carlo CVaR (95%) | -11.60 |
| Monte Carlo CVaR (99%) | -15.12 |

---

## Stress Testing

| Scenario | Loss |
|---|---|
| 2σ Stress | -11.10 |
| 3σ Stress | -16.65 |
| 5σ Stress | -27.76 |
| Worst Historical Loss | -101.91 |

Findings:

Extreme electricity market events can generate losses far exceeding traditional risk measures.

---

## Key Findings

The German electricity market exhibits:

- Significant tail risk
- Extreme price spikes
- Heavy-tailed distributions
- Large discrepancies between Gaussian and historical risk estimates

Historical simulation and CVaR measures provide a more realistic representation of downside risk than standard Gaussian models.

---

## Libraries Used

- pandas
- numpy
- scipy
- matplotlib
- statsmodels

---

## Skills Demonstrated

- Quantitative risk management
- Value-at-Risk estimation
- Conditional Value-at-Risk
- Monte Carlo simulation
- Stress testing
- Tail risk analysis
- Energy market analytics

---

## Future Extensions

Possible future developments include:

- Filtered Historical Simulation
- EVT (Extreme Value Theory)
- GARCH-based VaR
- Expected Shortfall backtesting
- Portfolio VaR
- Multi-asset energy risk modeling
