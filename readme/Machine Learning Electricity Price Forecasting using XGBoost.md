⚡ Machine Learning Electricity Price Forecasting using XGBoost
Project Overview

This project develops a machine learning framework for forecasting German day-ahead electricity prices using historical market information, demand, and renewable generation data.

The objective is to investigate whether modern machine learning algorithms can outperform classical econometric approaches and persistence benchmarks in short-term electricity price forecasting.

The project combines:

Feature engineering
Time series forecasting
Machine learning
Explainable AI
Hyperparameter optimization
Cross-validation
Dataset

Source:

Open Power System Data (OPSD)
ENTSO-E Transparency Platform

Country:

Germany

Period:

2018-10-01 – 2020-09-30

Frequency:

Hourly

Variables:

Variable	Description
price	German day-ahead electricity price (€/MWh)
load	Electricity demand (MW)
wind	Wind generation (MW)
solar	Solar generation (MW)

Total observations:

17,540
Exploratory Data Analysis
Correlation Analysis
Variable	Correlation with Price
Load	+0.487
Wind	-0.392
Solar	-0.194

The results confirm the existence of the Merit Order Effect, whereby renewable generation exerts downward pressure on wholesale electricity prices.

Statistical Properties

Electricity prices exhibit:

non-normality
heavy tails
negative prices
price spikes
strong seasonality
Jarque-Bera Test
p-value < 0.001

indicating significant departures from normality.

Stationarity Tests
Test	Result
ADF	Stationary
KPSS	Non-stationary

The results suggest the presence of strong deterministic seasonal patterns.

Seasonality Analysis

Significant seasonality was detected at:

Lag	Correlation
24 hours	0.636
168 hours	0.585

Ljung-Box tests confirmed strong serial dependence.

Feature Engineering

The following feature groups were constructed:

Lag Features
price_lag_1
price_lag_2
price_lag_3
price_lag_6
price_lag_12
price_lag_24
price_lag_48
price_lag_168
Fundamental Features
load
wind
solar
load_lag_1
wind_lag_1
solar_lag_1
load_lag_24
wind_lag_24
solar_lag_24
Rolling Statistics
rolling_mean_24
rolling_std_24
rolling_mean_48
rolling_std_48
rolling_mean_168
rolling_std_168
Calendar Features
hour
dayofweek
month
weekend
Baseline Forecast

Persistence benchmark:

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
Econometric Benchmark

A SARIMAX model with exogenous variables was estimated.

Performance:

Metric	Value
MAE	12.71
RMSE	15.83

The SARIMAX model failed to outperform the persistence benchmark.

Machine Learning Model

Algorithm:

XGBoost Regressor

Initial hyperparameters:

n_estimators = 300
max_depth = 6
learning_rate = 0.05
subsample = 0.8
colsample_bytree = 0.8
Initial Performance
Metric	Value
MAE	2.47
RMSE	4.90
sMAPE	14.22%

The machine learning model substantially outperformed both benchmark models.

Hyperparameter Optimization

Grid search was performed over:

tree depth
number of estimators
learning rate

Best model:

Parameter	Value
max_depth	6
n_estimators	500
learning_rate	0.05

Final performance:

Metric	Value
MAE	2.17
Model Comparison
Model	MAE
Persistence	9.04
SARIMAX	12.71
XGBoost	2.17

The optimized XGBoost model achieved:

76% reduction in forecasting error

relative to the persistence benchmark.

Explainable AI (SHAP)

SHAP values were used to interpret model predictions.

Top features:

Feature	Importance
price_lag_1	12.22
load	1.54
hour	1.22
price_lag_2	1.18
wind	1.07
solar	0.97
Key Findings

The analysis reveals that electricity prices are primarily driven by:

Short-term persistence
price_lag_1
price_lag_2
Fundamental market variables
load
wind
solar
Intraday seasonality
hour
Weekly seasonality
price_lag_168
Time Series Cross Validation

Expanding-window cross validation was performed.

Results:

Fold	MAE
1	3.73
2	2.55
3	2.37
4	3.27
5	2.19

Average performance:

Mean MAE = 2.82
Standard Deviation = 0.59

demonstrating strong out-of-sample robustness.

Technologies Used
Python
Pandas
NumPy
Scikit-learn
XGBoost
SHAP
Statsmodels
Matplotlib
Skills Demonstrated
Statistics
hypothesis testing
correlation analysis
normality testing
Time Series Analysis
stationarity testing
seasonality analysis
lag analysis
Machine Learning
feature engineering
XGBoost
hyperparameter optimization
Explainable AI
SHAP values
feature importance analysis
Energy Economics
Merit Order Effect
renewable integration
electricity market dynamics
Quantitative Research
benchmark construction
cross-validation
model comparison
predictive modeling
Conclusion

The results demonstrate that machine learning models can significantly outperform classical econometric models in short-term electricity price forecasting.

The explainability analysis further revealed that electricity prices are primarily driven by short-term persistence, demand conditions, renewable generation and market seasonality.
