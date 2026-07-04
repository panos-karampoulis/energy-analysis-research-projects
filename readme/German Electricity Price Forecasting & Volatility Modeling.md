⚡ German Electricity Price Forecasting & Volatility Modeling
Project Overview

This project investigates the statistical properties, forecasting performance and volatility dynamics of the German day-ahead electricity market.

The objective was to evaluate whether classical econometric models can outperform simple persistence benchmarks while simultaneously studying the impact of renewable generation on electricity prices and the presence of volatility clustering.

The analysis combines:

Time series econometrics
Energy market fundamentals
Volatility modeling
Forecast evaluation techniques
Dataset

Source:

Open Power System Data (OPSD)
ENTSO-E Transparency Platform

Period:

2018-10-01 – 2020-09-30

Frequency:

Hourly observations

Variables:

Variable	Description
price	German day-ahead electricity price (€/MWh)
load	Electricity demand (MW)
wind	Wind generation (MW)
solar	Solar generation (MW)

Total observations:

17,540 hourly observations
Exploratory Data Analysis
Correlation Analysis
Variable	Correlation with Price
Load	+0.487
Wind	-0.392
Solar	-0.194
Key finding

The results confirm the well-known Merit Order Effect, where increased renewable generation exerts downward pressure on wholesale electricity prices.

Distributional Properties

Electricity prices exhibit:

Negative skewness
Excess kurtosis
Fat tails
Price spikes
Negative prices
Statistic	Value
Skewness	-0.512
Kurtosis	4.964

Jarque-Bera test:

p-value < 0.001

indicating strong deviations from normality.

Stationarity Analysis

Two complementary stationarity tests were performed:

Test	Result
Augmented Dickey-Fuller	Stationary
KPSS	Non-stationary

This combination suggests that electricity prices contain deterministic seasonal components rather than behaving as pure random walks.

Seasonality Analysis

Strong seasonal patterns were detected:

Daily seasonality
Lag 24 autocorrelation = 0.636
Weekly seasonality
Lag 168 autocorrelation = 0.585
Ljung-Box Test
p-value < 0.001

indicating significant serial dependence.

Benchmark Forecasting Model

A persistence benchmark was implemented:

P
t
	​

=P
t−24
	​


Performance:

Metric	Value
MAE	9.04
RMSE	14.92
SARIMAX Forecasting Model

The following model was estimated:

SARIMAX(1,0,1)(1,1,1,24)

Exogenous regressors:

Load
Wind generation
Solar generation
Results
Metric	Value
MAE	12.71
RMSE	15.83

The SARIMAX model underperformed the persistence benchmark.

Economic Interpretation

The estimated coefficients confirm established electricity market relationships:

Variable	Coefficient
Load	Positive
Wind	Negative
Solar	Negative

These findings provide empirical evidence supporting the Merit Order Effect in the German electricity market.

Volatility Modeling

Residual diagnostics revealed significant heteroskedasticity.

ARCH-LM test:

p-value < 0.001

This motivated the estimation of volatility models.

GARCH(1,1)

Estimated parameters:

Parameter	Value
α	0.720
β	0.165

Volatility persistence:

α + β = 0.885

indicating strong volatility clustering.

EGARCH(1,1)

Model comparison:

Model	AIC
GARCH	77873
EGARCH	77820

The EGARCH specification substantially outperformed the symmetric GARCH model, suggesting asymmetric responses of volatility to market shocks.

Main Findings

The German electricity market exhibits:

✅ Strong seasonality

✅ Significant autocorrelation

✅ Non-normal distributions

✅ Renewable-driven price effects

✅ Volatility clustering

✅ Asymmetric volatility dynamics

Technologies Used
Python
Pandas
NumPy
SciPy
Statsmodels
ARCH
Scikit-learn
Matplotlib
Skills Demonstrated
Statistics
Hypothesis testing
Normality testing
Correlation analysis
Time Series Econometrics
Stationarity testing
SARIMA/SARIMAX modeling
Residual diagnostics
Financial Econometrics
ARCH effects
GARCH modeling
EGARCH modeling
Energy Economics
Merit Order Effect
Electricity market dynamics
Renewable integration effects
Quantitative Analysis
Benchmark construction
Model comparison
Forecast evaluation
Conclusion

The results demonstrate that:

sophisticated econometric models do not necessarily outperform simple persistence benchmarks in short-term electricity price forecasting.

However, volatility modeling successfully captured the heteroskedastic and asymmetric behavior of electricity prices, providing valuable insights into electricity market risk dynamics.
