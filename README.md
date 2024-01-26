# Portfolio-Allocation
Reinforcement Learning for Portfolio Allocation

# 01. INTRODUCTION
## OBJECTIVE AND CONSTRAINTS
Our objective is to **outperform** the *equal-weight* and *mean-variance* optimization strategies using reinforcement learning-based portfolio optimization model, designing the **RL** model to learn a *policy* that dynamically allocates weights to different assets with the goal of *maximizing* returns while considering the following constraints: 
- **Daily Rebalancing**: capability to adjust the portfolio allocation among stocks on a daily basis.
- **No Short Selling**: non-negative stock weights to be aligned with a long-only investment approach (no short positions in stocks). 
- **No commission Fees**: for the sake of modeling and analysis, we decide to evaluate the performance of the trading strategy without considering additional transaction costs. 
- **Total Weights Equal 1**: to maintain a normalized portfolio, ensuring that it is fully invested, and the weights of all stocks sum up to 1. 

SOURCE DATA
We decided to download data directly from Yahoo Finance instead of using the pre-prepared dataset containing only stock prices. Obtaining real-time or recent data directly from a financial data source might be more convenient: 
Freshness of Data: since financial markets are dynamic and stock prices can change rapidly, downloading data from Yahoo Finance allows you to access the most recent and up-to-date information. 
Inclusion of Additional Features: Yahoo Finance provides a wide range of financial data and metrics behind stock prices, including company fundamentals, technical indicators, and economic indicators. 
Consistency Across Datasets: by obtaining data directly from Yahoo Finance, you can ensure consistency with external benchmarks and indices. 

ECONOMIC INDICATORS
Close Price: last traded price of a financial instrument at the end of a trading day. It is often used to calculate returns and assess the overall performance of an asset. 
High Price: highest traded price of a financial instrument during a specific time period, such as a training day. It indicates the maximum price reached by the asset within that period.
Low Price: lowest traded price of a financial instrument during a specific time period. It reflects the minimum price reached by the asset within that period.
Open Price: first traded price of a financial instrument at the beginning of a trading day. It provides insight into the initial market sentiment and can influence the day’s trading activity. 
Volume: total number of shares traded for a particular financial instrument during a given time period. High trading volumes are often associated with increased market activity and liquidity. 
