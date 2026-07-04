Electricity Market Regime Detection using PCA, K-Means and Gaussian Mixture Models
Project Overview

Electricity markets exhibit complex dynamics characterized by price spikes, congestion effects, renewable generation variability, and structural market fragmentation. Traditional forecasting models often assume a homogeneous market structure, whereas real-world electricity markets operate under multiple latent regimes.

This project applies unsupervised machine learning techniques to identify hidden market regimes in the Italian electricity market using zonal day-ahead electricity prices.

The objective is to answer the following research question:

Can electricity market behavior be decomposed into a small number of statistically distinct latent regimes?

Dataset

Dataset source:

Open Power System Data (OPSD)
Frequency: Hourly
Period: 2015–2020
Country: Italy

Italian bidding zones used:

IT_NORD
IT_CNOR
IT_CSUD
IT_SUD
IT_SARD
IT_SICI

Total observations:

50,280 hourly observations
Feature Engineering

For each timestamp, several market descriptors were constructed:

Feature	Description
mean_price	Average zonal electricity price
std_price	Cross-sectional price dispersion
mean_return	Average log return
volatility	Rolling 24-hour volatility
max_price	Maximum zonal price
min_price	Minimum zonal price
spread	Maximum minus minimum zonal price

These features capture:

market price level,
volatility,
regional congestion,
market fragmentation,
stress conditions.
Exploratory Data Analysis
Summary Statistics
Statistic	Value
Mean Price	50.7 €/MWh
Mean Spread	14.4 €/MWh
Mean Volatility	0.124

Maximum observed spread:

214 €/MWh

indicating severe market fragmentation during stress periods.

Principal Component Analysis (PCA)

PCA was performed to identify the latent factors driving the Italian electricity market.

Explained Variance
Component	Explained Variance
PC1	48.6%
PC2	25.0%
PC3	14.7%
PC4	10.9%
Cumulative Variance
Components	Explained
1	48.6%
2	73.6%
3	88.3%
4	99.2%
Finding

More than 99% of the total market variance can be explained using only four latent factors.

This suggests that the Italian electricity market exhibits a strong low-dimensional factor structure.

K-Means Clustering

To identify market regimes, K-Means clustering was applied.

Cluster Selection

Two methods were used:

Elbow Method
Silhouette Score

The optimal number of clusters was chosen as:

K = 4
K-Means Market Regimes
Regime	Mean Price	Volatility	Spread	Interpretation
Cluster 0	40.8	0.113	7.7	Normal Market
Cluster 1	64.7	0.115	43.3	Congestion Regime
Cluster 2	33.2	0.273	14.3	High Volatility Regime
Cluster 3	62.9	0.105	8.2	High Price Regime
Interpretation

The clustering analysis revealed four distinct market states:

Normal operating conditions
Transmission congestion periods
High volatility regimes
High price market environments
Gaussian Mixture Models (GMM)

A probabilistic clustering approach was then applied.

Unlike K-Means, GMM assumes that observations belong to market regimes probabilistically rather than deterministically.

GMM Regimes
Regime	Mean Price	Volatility	Spread	Interpretation
GMM 0	48.2	0.102	5.5	Stable Market
GMM 1	52.2	0.109	16.8	Moderate Congestion
GMM 2	52.8	0.164	25.8	Volatile Congestion
GMM 3	54.2	0.182	25.7	Extreme Stress
Key Findings

The analysis demonstrates that:

electricity markets exhibit a low-dimensional latent structure,
multiple statistically distinct market regimes exist,
congestion and volatility represent major drivers of market behavior,
probabilistic clustering provides a realistic representation of electricity market dynamics.
Technologies Used
Python
Pandas
NumPy
Scikit-Learn
SciPy
PCA
K-Means
Gaussian Mixture Models
Quantitative Finance Applications

The methodology used in this project is directly applicable to:

Energy Trading
Quantitative Research
Market Regime Detection
Regime-Switching Models
Portfolio Allocation
Risk Management
Commodity Trading Analytics
Conclusion

This project demonstrates that electricity markets can be represented as a set of latent market regimes characterized by:

price levels,
volatility,
congestion,
regional market fragmentation.

The results suggest that unsupervised machine learning techniques provide a powerful framework for understanding electricity market structure and identifying hidden market states relevant for quantitative trading and risk management.

Project Status
Status: Completed
Type: Quantitative Energy Markets / Machine Learning
Difficulty: Advanced
