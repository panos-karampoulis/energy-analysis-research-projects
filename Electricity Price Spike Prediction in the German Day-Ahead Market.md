⚡ Electricity Price Spike Prediction in the German Day-Ahead Market
📌 Project Overview

This project investigates the prediction of extreme electricity price events ("price spikes") in the German day-ahead electricity market using machine learning classification models.

Electricity markets are characterized by occasional extreme price movements caused by:

supply shortages,
renewable generation fluctuations,
demand surges,
transmission constraints,
market regime changes.

The objective of this project is to determine whether these rare events can be predicted one hour ahead using historical prices and fundamental market variables.

🎯 Research Question

Can machine learning models predict extreme electricity price spikes in the German electricity market one hour ahead?

📊 Dataset

Source:

Open Power System Data (OPSD)
ENTSO-E Transparency Platform

Variables used:

Variable	Description
price	German day-ahead electricity price
load	Electricity demand
wind	Wind generation
solar	Solar generation

Dataset characteristics:

Frequency: Hourly
Period: October 2018 – September 2020
Observations: 17,540
⚡ Defining Price Spikes

Price spikes were defined as observations above the 95th percentile of the electricity price distribution:

Spike={
1,
0,
	​

Price>Q
95
	​

otherwise
	​


Threshold:

95th percentile = 63.90 €/MWh

Class distribution:

Class	Observations
Normal	16,663
Spike	877
🔧 Feature Engineering

To capture temporal persistence and market conditions, the following features were created:

Price features
price_lag_1
price_lag_2
price_lag_3
price_lag_24
Fundamental features
load
wind
solar
load_lag_1
wind_lag_1
solar_lag_1
Market regime features
rolling_mean_24
rolling_std_24
Calendar effects
hour
day_of_week
month
📈 Train-Test Split

A chronological split was used:

Training set: 75%
Test set: 25%

This approach avoids look-ahead bias and mimics real-world forecasting conditions.

Model 1 — Logistic Regression
Results
Metric	Value
Accuracy	98.77%
Precision	59.1%
Recall	97.4%
F1-score	0.735
ROC-AUC	0.998

Confusion Matrix:

	Predicted Normal	Predicted Spike
Actual Normal	4250	52
Actual Spike	2	75
Interpretation

The logistic regression model achieved extremely high recall, successfully detecting almost all spike events.

Model 2 — Random Forest
Results
Metric	Value
Accuracy	99.11%
Precision	70.7%
Recall	84.4%
F1-score	0.769
ROC-AUC	0.996

Confusion Matrix:

	Predicted Normal	Predicted Spike
Actual Normal	4275	27
Actual Spike	12	65
Feature Importance
Feature	Importance
price_lag_1	32.4%
price_lag_2	16.7%
rolling_mean_24	15.2%
price_lag_24	8.6%
price_lag_3	6.8%
load	5.1%
Model 3 — XGBoost
Results
Metric	Value
Accuracy	99.38%
Precision	82.9%
Recall	81.8%
F1-score	0.824
ROC-AUC	0.998

Confusion Matrix:

	Predicted Normal	Predicted Spike
Actual Normal	4289	13
Actual Spike	14	63
Feature Importance
Feature	Importance
price_lag_1	63.4%
hour	6.0%
price_lag_2	5.6%
solar	3.4%
rolling_mean_24	2.6%
rolling_std_24	2.3%
Key Findings

The analysis reveals four major drivers of electricity price spikes:

1. Strong Temporal Persistence

Electricity price spikes tend to cluster over time.

Most important predictors:

price_lag_1
price_lag_2
price_lag_3
price_lag_24
2. Intraday Seasonality

The hour of the day strongly affects spike occurrence.

3. Renewable Generation Effects

Lower renewable generation increases the probability of price spikes.

Key variables:

wind generation
solar generation
4. Market Regime Dependence

Periods of high market volatility tend to persist.

Key variables:

rolling_mean_24
rolling_std_24
Model Comparison
Model	Accuracy	Precision	Recall	F1	ROC-AUC
Logistic Regression	98.77%	59.1%	97.4%	0.735	0.998
Random Forest	99.11%	70.7%	84.4%	0.769	0.996
XGBoost	99.38%	82.9%	81.8%	0.824	0.998
Conclusion

This study demonstrates that extreme electricity price events are highly predictable using machine learning techniques.

The XGBoost model achieved:

99.38% accuracy
82.9% precision
81.8% recall
ROC-AUC of 0.998

The results suggest that electricity price spikes exhibit:

strong temporal persistence,
market regime dependence,
intraday seasonality,
sensitivity to renewable generation dynamics.

These findings have direct applications in:

energy trading,
risk management,
battery storage optimization,
electricity market forecasting.
🛠️ Technologies Used
Python
Pandas
NumPy
Scikit-learn
XGBoost
Matplotlib
Statsmodels
📚 Skills Demonstrated
Time Series Analysis
Feature Engineering
Machine Learning Classification
Imbalanced Learning
Rare Event Prediction
Energy Economics
Quantitative Research
Model Evaluation
Explainable AI
Electricity Market Analytics
