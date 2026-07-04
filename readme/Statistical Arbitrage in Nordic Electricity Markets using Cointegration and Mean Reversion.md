Statistical Arbitrage in Nordic Electricity Markets using Cointegration and Mean Reversion

## Project Overview

This project investigates the existence of statistical arbitrage opportunities in European electricity markets by applying econometric and quantitative finance techniques to Nordic day-ahead power prices.

The objective is to identify whether electricity prices from interconnected markets exhibit:

- strong correlation,
- long-run equilibrium relationships (cointegration),
- mean-reverting behavior,
- and exploitable statistical arbitrage opportunities.

The analysis focuses on the Danish electricity markets:

- DK1 (Western Denmark)
- DK2 (Eastern Denmark)

using hourly day-ahead electricity prices obtained from the ENTSO-E Transparency Platform.

---

## Research Questions

The project aims to answer the following questions:

1. Are DK1 and DK2 electricity prices highly correlated?
2. Do they exhibit cointegration?
3. Is the spread between the two markets stationary?
4. Does the spread display mean-reverting behavior?
5. Can a statistical arbitrage strategy exploit these dynamics?
6. Does the strategy survive out-of-sample testing?

---

## Dataset

Source:

- ENTSO-E Transparency Platform
- Open Power System Data (OPSD)

Dataset characteristics:

- Frequency: Hourly
- Period: January 2015 – September 2020
- Observations: ~50,000

Markets analyzed:

- DK1 Day-Ahead Prices
- DK2 Day-Ahead Prices

---

## Methodology

### 1. Exploratory Data Analysis

Performed:

- descriptive statistics,
- skewness and kurtosis,
- Jarque-Bera normality test,
- stationarity analysis,
- visualization of electricity prices.

---

### 2. Stationarity Tests

Applied:

- Augmented Dickey-Fuller Test (ADF)
- KPSS Test

Purpose:

- determine the integration order of electricity prices.

---

### 3. Correlation Analysis

Methods:

- Pearson Correlation Coefficient
- Correlation Matrix

Result:

```
Correlation = 0.909
```

---

### 4. Cointegration Analysis

Method:

- Engle-Granger Cointegration Test

Results:

```
Test Statistic = -21.38
p-value = 0.000
```

Conclusion:

DK1 and DK2 electricity prices exhibit strong cointegration.

---

### 5. Hedge Ratio Estimation

Method:

- Ordinary Least Squares (OLS)

Estimated relationship:

```
DK1 = 2.684 + 0.8588 × DK2
```

Estimated hedge ratio:

```
β = 0.8588
```

Spread definition:

```
Spread = DK1 − β × DK2
```

---

### 6. Spread Stationarity

Method:

- Augmented Dickey-Fuller Test

Results:

```
ADF Statistic = -21.38
p-value = 0.000
```

Conclusion:

The spread is stationary and suitable for statistical arbitrage analysis.

---

### 7. Mean Reversion Analysis

Methods:

- Hurst Exponent
- Half-Life Estimation
- Ornstein-Uhlenbeck Mean Reversion Framework

Results:

```
Hurst Exponent = 0.082
Half-Life = 4.59 hours
```

Interpretation:

The spread exhibits extremely strong mean-reverting behavior.

---

### 8. Statistical Arbitrage Strategy

Implemented:

- Rolling Z-score strategy
- Long spread entry signals
- Short spread entry signals
- Dynamic exit rules

Signal generation:

```
Long Entry:
Z-score < threshold

Short Entry:
Z-score > threshold

Exit:
|Z-score| < threshold
```

---

### 9. Hyperparameter Optimization

A grid search optimization framework was implemented to determine optimal strategy parameters.

Parameters optimized:

- Rolling window length
- Entry threshold
- Exit threshold

Optimization metrics:

- Sharpe Ratio
- Drawdown
- Profitability

Best parameters:

```
Lookback = 24
Entry = 0.75
Exit = 0.50
```

---

### 10. Out-of-Sample Validation

Dataset split:

```
Training:
2015–2018

Testing:
2019–2020
```

Out-of-sample performance:

```
Sharpe Ratio = 12.98
Profit = 5328
Maximum Drawdown = -67.38
```

---

## Statistical Techniques Applied

### Econometrics

- Pearson Correlation
- Engle-Granger Cointegration
- OLS Regression
- Augmented Dickey-Fuller Test
- KPSS Test
- Jarque-Bera Test
- Ljung-Box Test
- ARCH Effects Test

### Time Series Analysis

- Stationarity Analysis
- Mean Reversion Analysis
- Hurst Exponent
- Half-Life Estimation
- Ornstein-Uhlenbeck Dynamics

### Quantitative Finance

- Statistical Arbitrage
- Pair Trading
- Hedge Ratio Estimation
- Z-Score Trading Signals
- Backtesting
- Sharpe Ratio
- Drawdown Analysis
- Hyperparameter Optimization
- Out-of-Sample Validation

---

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Statsmodels
- SciPy
- Scikit-learn
- Google Colab

---

## Key Findings

- Nordic electricity prices exhibit strong correlation.
- DK1 and DK2 markets are strongly cointegrated.
- The spread is highly stationary.
- Mean reversion is statistically significant.
- Half-life estimation confirms rapid spread correction.
- Statistical arbitrage opportunities may exist in interconnected electricity markets.
- Proper validation and transaction cost analysis remain essential before practical implementation.

---

## Future Improvements

Possible extensions include:

- Johansen Cointegration Test
- Vector Error Correction Models (VECM)
- Kalman Filter Dynamic Hedge Ratios
- Regime Switching Models
- Transaction Cost Modeling
- Market Impact Analysis
- Walk-Forward Optimization
- Reinforcement Learning Statistical Arbitrage

---

## Disclaimer

This project was developed for educational and research purposes only and does not constitute investment advice.
