Battery Energy Storage Arbitrage and Optimization
Overview

This project develops a battery energy storage system (BESS) trading framework for electricity markets using historical German day-ahead electricity prices. The objective is to evaluate whether battery arbitrage strategies remain profitable after accounting for realistic operational constraints and battery degradation costs.

The project progresses from a simple rule-based trading strategy to a more advanced threshold-based dispatch model and demonstrates the importance of battery lifecycle economics in energy trading applications.

Objectives

The main objectives of this project are:

Build a realistic battery dispatch simulator.
Implement electricity price arbitrage strategies.
Model battery state-of-charge dynamics.
Evaluate trading performance using financial metrics.
Optimize battery technical parameters.
Incorporate battery degradation costs.
Develop advanced threshold-based trading strategies.
Dataset

The analysis uses hourly German electricity market data containing:

Electricity prices
Electricity load
Wind generation
Solar generation
Study period
October 2018 – September 2020
Dataset dimensions
17,534 hourly observations
4 variables
Methodology
1. Battery Model

A battery energy storage system was modeled with:

Energy capacity (MWh)
Charge/discharge rate (MW)
Round-trip efficiency
State of charge (SOC)

The battery state evolves according to charging and discharging decisions.

2. Naive Moving Average Arbitrage Strategy

The initial strategy was based on a simple moving average rule:

Charge:
Price < Moving Average

Discharge:
Price > Moving Average
3. Performance Evaluation

The following performance metrics were calculated:

Total profit
Sharpe ratio
Maximum drawdown
Number of battery cycles
Average battery utilization
Initial Results
Battery configuration
Parameter	Value
Capacity	100 MWh
Charge rate	25 MW
Efficiency	90%
Moving average	24 hours
Performance
Metric	Value
Total Profit	€772,231
Sharpe Ratio	6.09
Maximum Drawdown	-€8,750
Battery Cycles	3,806
Average Utilization	50.4%
Battery Parameter Optimization

A grid search optimization was performed over:

Capacity
50, 100, 200 MWh
Charge Rate
10, 25, 50 MW
Efficiency
85%, 90%, 95%
Moving Average Window
12, 24, 48, 72 hours

A total of:

108 battery configurations

were evaluated.

Optimal Battery Configuration
Parameter	Value
Capacity	200 MWh
Charge Rate	50 MW
Efficiency	95%
Moving Average	24 hours
Performance
Metric	Value
Profit	€1.89 million
Sharpe Ratio	7.45
Maximum Drawdown	-€14,892
Battery Degradation Modeling

To account for battery wear, a degradation cost of:

€5 per MWh throughput

was introduced.

Result
Metric	Value
Profit	-€54,538
Battery Cycles	3,806

This demonstrates that naive arbitrage strategies become unprofitable when realistic battery lifecycle costs are considered.

Threshold-Based Battery Arbitrage

To reduce excessive cycling, a threshold-based strategy was implemented:

Charge:
Price < MA − kσ

Discharge:
Price > MA + kσ

where:

MA = rolling mean price
σ = rolling standard deviation
k = threshold parameter
Threshold Strategy Results
k = 1
Metric	Value
Profit	€499,227
Sharpe Ratio	3.19
Maximum Drawdown	-€17,625
Battery Cycles	1,525
Threshold Optimization
Threshold (k)	Profit (€)	Sharpe	Cycles
0.5	463,594	2.20	2,697
1.0	499,227	3.19	1,525
1.5	390,533	4.16	613
2.0	414,108	6.83	261
Key Findings

The project demonstrates several important findings:

Simple battery arbitrage strategies can generate large gross profits.
Battery degradation costs fundamentally change profitability.
Excessive battery cycling destroys economic performance.
Threshold-based strategies dramatically reduce battery wear.
Selective dispatch policies improve long-term profitability.
Risk-adjusted returns improve significantly when trading frequency decreases.
Technologies Used
Python
Pandas
NumPy
Matplotlib
SciPy
Scikit-learn
Future Extensions

Potential improvements include:

Reinforcement learning battery dispatch
Dynamic battery degradation models
Intraday electricity market arbitrage
Multi-market optimization
Battery portfolio optimization
Stochastic dynamic programming
Deep reinforcement learning agents
Conclusion

This project shows that while naive battery arbitrage strategies can appear highly profitable, realistic battery degradation costs can eliminate those profits entirely. Threshold-based dispatch strategies significantly reduce cycling activity and restore profitability, highlighting the importance of battery lifecycle economics in energy storage trading applications.
