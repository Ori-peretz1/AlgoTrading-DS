AlgoTrading – Market Regime
📌 Project Objective
This project aims to dynamically identify the current market regime and apply the optimal trading strategy for that environment. Based on our research, investor behavior changes significantly across regimes. For example:
- Crisis / high uncertainty: Mean-reversion strategies like pair trading often perform better.
- Stable / trending markets: Momentum trading may yield higher returns.

By detecting regime shifts early and adapting strategy in real-time, we aim to maximize returns and reduce risk.
📚 Background
A market regime assumes the market operates in a finite number of distinct behavioral states, each defined by:
- Volatility patterns
- Directionality (trend)
- Correlations between assets
- Macroeconomic conditions

Key references:
- Quandt (1958), Goldfeld & Quandt (1973) – Econometric foundations of regime switching.
- Borisov (2024) – ML techniques for distinguishing market regimes.
## 🛠️ Project Workflow
```text
 ┌──────────────────┐
 │ 1. Data           │
 │ Preparation       │
 └───────┬───────────┘
         │
         ▼
 ┌──────────────────┐
 │ 2. PCA            │
 │ Dimensionality    │
 │ Reduction         │
 └───────┬───────────┘
         │
         ▼
 ┌──────────────────┐
 │ 3. KMeans         │
 │ Clustering        │
 └───────┬───────────┘
         │
         ▼
 ┌──────────────────┐
 │ 4. Strategy       │
 │ Backtesting       │
 └───────┬───────────┘
         │
         ▼
 ┌──────────────────┐
 │ 5. Cluster-Based  │
 │ Performance       │
 │ Analysis          │
 └───────┬───────────┘
         │
         ▼
 ┌──────────────────┐
 │ 6. Strategy       │
 │ Selector Algorithm│
 └──────────────────┘
```
📑 Step-by-Step Breakdown
1. 📁 Data Preparation
- Historical stock price data from S&P 500 (2018–2020, including edges).
- Computed percentage returns and rolling standard deviations.
- Features serve as input to PCA and clustering.
2. 🔻 PCA – Principal Component Analysis
- Applied rolling PCA to reduce noise and highlight dominant market factors.
- Retained 36 components to capture >90% of variance.
- Top 2–3 components plotted for visualization, aiding clustering.
3. 📊 KMeans Clustering
- Grouped assets into 7 clusters based on PCA-reduced features.
- Each cluster represents a distinct market regime.
4. 📈 Strategy Backtesting
Pair Trading (Mean-Reversion):
- Finds co-integrated pairs and trades spread deviations.

Momentum Trading (Trend-Following):
- Buys strong performers, sells weak performers based on trend signals.
5. 📊 Cluster-Based Performance Analysis
- Calculated average returns for both strategies per cluster:
  pair_returns_by_cluster = { cluster_num: return% }
  momentum_returns_by_cluster = { cluster_num: return% }
- Determined best strategy per cluster.
6. 🧠 Strategy Selector Algorithm
- For each new observation:
  - Identify its cluster via PCA + KMeans.
  - Apply the best-performing strategy for that cluster.
- Enables real-time strategy switching on regime shifts.
🚀 Summary of Benefits
- Noise reduction with PCA improves clustering accuracy.
- KMeans clustering segments the market into actionable regimes.
- Adaptive strategy selection outperforms static approaches.
- Modular design allows adding more strategies or regime definitions.
📌 Future Enhancements
- Integrate additional macroeconomic indicators for regime classification.
- Apply Hidden Markov Models (HMM) for probabilistic regime detection.
- Automate live trading integration with broker APIs.
