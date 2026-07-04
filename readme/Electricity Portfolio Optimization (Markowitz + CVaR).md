Electricity Portfolio Optimization (Markowitz + CVaR)
⚡ Overview

This project implements a multi-asset portfolio optimization framework for energy markets, combining classical Markowitz mean-variance optimization with Conditional Value at Risk (CVaR) minimization.

The goal is to model optimal allocation across energy-related assets under uncertainty and extreme risk conditions.

🎯 Objectives
Construct energy asset returns from market data
Build covariance and return structure
Optimize portfolio using:
Markowitz mean-variance optimization
Efficient frontier analysis
CVaR (tail-risk) minimization
Compare risk-return trade-offs across strategies
🧩 Assets Modeled
Electricity price series
Wind generation proxy
Solar generation proxy
Load demand proxy
🏗️ Methodology
1. Data Preparation
Time series alignment
Return computation using percentage changes
Feature cleaning and missing value handling
2. Markowitz Optimization

Portfolio optimization solves:

Minimize portfolio variance
Subject to:
full capital allocation constraint
target return constraint

This produces optimal asset weights under mean-variance assumptions.

3. Efficient Frontier

A range of target returns is simulated to construct the efficient frontier, showing:

Risk (volatility)
Return trade-off

This highlights diversification benefits between energy assets.

4. CVaR Optimization

To account for extreme market risk, Conditional Value at Risk (CVaR) is minimized.

This focuses on:

Tail risk
Extreme loss scenarios
Downside protection rather than variance alone
📊 Key Insights
Electricity price dominates portfolio exposure due to higher return structure
Renewable assets (wind/solar) contribute diversification benefits
CVaR optimization leads to more balanced and risk-averse allocations
Efficient frontier confirms non-perfect correlation between assets
🧠 Financial Interpretation
Markowitz optimization captures average risk behavior
CVaR optimization captures extreme downside risk
Energy markets exhibit significant tail risk and volatility clustering
⚙️ Technologies
Python
NumPy / Pandas
SciPy Optimization
Matplotlib (for frontier visualization)
📌 Outcome

This project demonstrates how classical portfolio theory can be extended to energy markets, incorporating both statistical risk and extreme event risk modeling.
