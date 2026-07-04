Reinforcement Learning Battery Trading (Q-Learning)
🔋 Overview

This project implements a tabular Reinforcement Learning (Q-Learning) agent for optimal battery energy arbitrage using electricity price time series data.

The agent learns when to charge, discharge, or hold a battery in order to maximize cumulative profit under time-varying electricity prices.

🎯 Objective

To replace heuristic battery trading strategies (moving averages, thresholds) with a self-learning agent that discovers optimal arbitrage behavior.

⚙️ Methodology
State Representation

The environment is discretized into a finite state space:

Price bin (quantile-based discretization)
Battery level (discrete levels)
Hour of day (0–23)
State = (price_bin, battery_level, hour)
Actions
0 → Hold
1 → Charge
2 → Discharge
Reward Function

Profit-based reward:

Charging → negative reward (cost of energy)
Discharging → positive reward (revenue)
Holding → neutral
Reward = revenue - cost
Learning Algorithm

Q-learning update rule:

Q(s,a)←Q(s,a)+α[r+γmaxQ(s
′
,a
′
)−Q(s,a)]
📊 Results
Training Performance
Stable convergence observed across episodes
Strong upward profit trajectory
Final Performance
Best Profit: ~953K
Average Last Episodes: ~922K
Converged policy after ~40–50 episodes
🧠 Key Insights
Strong dependency on price temporal structure
Battery arbitrage is highly predictable with hourly seasonality
Simple tabular RL already outperforms rule-based strategies
📌 Conclusion

This project demonstrates that even tabular reinforcement learning can learn profitable energy arbitrage strategies in structured markets.
