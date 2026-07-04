
 ⚡ Project — Electricity Price Volatility Forecasting using GARCH Family Models

## Overview

This project investigates volatility dynamics in the German electricity market using econometric volatility models from the GARCH family.

Unlike traditional price forecasting, this project focuses on forecasting market uncertainty and risk, which is crucial for:

- Energy trading
- Portfolio risk management
- Value-at-Risk (VaR)
- Option pricing
- Battery storage optimization
- Power market operations

The objective is to determine whether electricity markets exhibit:

- Volatility clustering
- Heavy tails
- Persistence
- Asymmetric volatility responses

and to identify the best-performing volatility model.

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

Variables:

- Day-ahead electricity price

---

## Methodology

### Step 1: Data preprocessing

Because electricity prices can become negative, percentage returns are not appropriate.

Instead, absolute price changes were calculated:


r_t = P_t - P_{t-1}


---

### Step 2: Stylized facts analysis

The following properties were investigated:

- Skewness
- Kurtosis
- ARCH effects

Results:

| Statistic | Value |
|---|---|
| Skewness | 0.486 |
| Kurtosis | 26.21 |
| ARCH LM p-value | <0.001 |

Findings:

- Significant fat tails
- Non-normal distribution
- Strong volatility clustering

---

## Models Estimated

### 1. GARCH(1,1)

Model:


σ²_t = ω + αε²_{t−1} + βσ²_{t−1}


Results:

| Parameter | Estimate |
|---|---|
| ω | 7.475 |
| α | 0.891 |
| β | 0.109 |
| ν | 3.663 |

Performance:

| Metric | Value |
|---|---|
| Log-Likelihood | -50151.1 |
| AIC | 100312 |

Findings:

- Extremely high volatility persistence
- Strong reaction to market shocks
- Heavy-tailed distribution

---

### 2. EGARCH(1,1)

Model:


log(σ²_t)


Results:

| Parameter | Estimate |
|---|---|
| ω | 1.793 |
| α | 1.221 |
| β | 0.498 |
| ν | 3.175 |

Performance:

| Metric | Value |
|---|---|
| Log-Likelihood | -50152.2 |
| AIC | 100314 |

Findings:

- Similar dynamics to standard GARCH
- No improvement in model fit

---

### 3. GJR-GARCH(1,1)

Model:


σ²_t = ω + αε²_{t−1}
+ γI(ε_{t−1}<0)ε²_{t−1}
+ βσ²_{t−1}


Results:

| Parameter | Estimate |
|---|---|
| ω | 6.109 |
| α | 1.000 |
| γ | -0.630 |
| β | 0.200 |
| ν | 3.932 |

Performance:

| Metric | Value |
|---|---|
| Log-Likelihood | -49969.5 |
| AIC | 99951 |

Findings:

- Significant asymmetric volatility effects
- Positive price shocks generate stronger volatility responses
- Best model according to information criteria

---

## Model Comparison

| Model | AIC |
|---|---|
| GARCH | 100312 |
| EGARCH | 100314 |
| GJR-GARCH | 99951 |

Winner:

✅ GJR-GARCH(1,1)

---

## Key Findings

The German electricity market exhibits:

- Strong volatility clustering
- Heavy-tailed distributions
- Extreme price events
- Significant asymmetric volatility effects

The GJR-GARCH model significantly outperformed both the standard GARCH and EGARCH specifications.

---

## Libraries Used

- pandas
- numpy
- scipy
- statsmodels
- arch
- matplotlib

---

## Skills Demonstrated

- Energy market analytics
- Volatility modeling
- Econometric analysis
- GARCH-family models
- Risk modeling
- Statistical testing
- Model selection using information criteria

---

## Future Work

Potential extensions include:

- VaR forecasting
- Expected Shortfall estimation
- Monte Carlo simulation
- Regime-switching GARCH
- Multivariate volatility models
