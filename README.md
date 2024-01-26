# Portfolio-Allocation
Reinforcement Learning for Portfolio Allocation - University Group Project

## 01. INTRODUCTION
**OBJECTIVE AND CONSTRAINTS**
Our objective is to **outperform** the *equal-weight* and *mean-variance* optimization strategies using reinforcement learning-based portfolio optimization model, designing the **RL** model to learn a *policy* that dynamically allocates weights to different assets with the goal of *maximizing* returns while considering the following constraints: 
- **Daily Rebalancing**: capability to adjust the portfolio allocation among stocks on a daily basis.
- **No Short Selling**: non-negative stock weights to be aligned with a long-only investment approach (no short positions in stocks). 
- **No commission Fees**: for the sake of modeling and analysis, we decide to evaluate the performance of the trading strategy without considering additional transaction costs. 
- **Total Weights Equal 1**: to maintain a normalized portfolio, ensuring that it is fully invested, and the weights of all stocks sum up to 1. 

**SOURCE DATA**
We decided to download data directly from **Yahoo Finance** instead of using the pre-prepared dataset containing only stock prices. Obtaining real-time or recent data directly from a financial data source might be more convenient: 
- **Freshness of Data**: since financial markets are dynamic and stock prices can change rapidly, downloading data from Yahoo Finance allows you to access the most recent and up-to-date information. 
- **Inclusion of Additional Features**: Yahoo Finance provides a wide range of financial data and metrics behind stock prices, including company fundamentals, technical indicators, and economic indicators. 
- **Consistency Across Datasets**: by obtaining data directly from Yahoo Finance, you can ensure consistency with external benchmarks and indices. 

**ECONOMIC INDICATORS**
- **Open Price**: *first* traded price of a financial instrument at the *beginning* of a trading day. It provides insight into the initial *market sentiment* and can influence the day’s trading activity. 
- **Close Price**: *last* traded price of a financial instrument at the *end* of a trading day. It is often used to calculate *returns* and assess the overall *performance* of an asset. 
- **High Price**: *highest* traded price of a financial instrument during a specific *time period*, such as a training day. 
- **Low Price**: *lowest* traded price of a financial instrument during a specific *time period*. 
- **Volume**: total number of *shares* traded for a particular financial instrument during a given time period. *High* trading volumes are often associated with increased market *activity* and *liquidity*. 

**FINANCIAL INDICATORS**
For providing insights into market *trends* and potential trading *signals*, let's collect the following list of **financial** indicators:
- **MACD** (Moving Average Convergence Divergence): A trend-following momentum indicator that shows the relationship between two moving averages of a security’s price.
- **Bollinger Bands** (Upper Band and Lower Band): A volatility indicator that consists of a middle band being an N-period simple moving average, an upper band at K times an N-period standard deviation above the middle band, and a lower band at K times an N-period standard deviation below the middle band.
- **RSI** (Relative Strength Index): A momentum oscillator that measures the speed and change of price movements. RSI ranges from 0 to 100 and is typically used to identify overbought or oversold conditions.
- **CCI** (Commodity Channel Index): An oscillator used to identify cyclical turns in commodity prices. It measures the relationship between the current price, a moving average of prices, and normal deviations from that average.
- **DX** (Directional Movement Index): A trend strength indicator used to identify the strength and direction of a trend. It consists of the Plus Directional Movement (+DI), Minus Directional Movement (-DI), and Average Directional Index (ADX).
- **30-day Simple Moving Average** (close_30_sma): A popular indicator that smoothens out price data by creating a constantly updated average price.
- **60-day Simple Moving Average** (close_60_sma): Similar to the 30-day SMA, but calculated over a 60-day period.

**STOCKS**
For constructing a **well-balanced** and **resilient** investment portfolio, we decide to consider the following *well-known* companies: Microsoft Corporation (**MSFT**), Coca-Cola Company (**KO**), Boeing Company (**BA**), Procter & Gamble Co. (**PG**), AT&T Inc. (**T**), Pfizer Inc. (**PFE**), JPMorgan Chase & Co. (**JPM**), Exxon Mobil Corporation (**XOM**), McDonald's Corporation (**MCD**), Southern Company (**SO**), Simon Property Group, Inc. (**SPG**), and DuPont de Nemours, Inc. (**DD**).  
In particular, we decided to download historical financial data for the specified list of stocks from **January 1, 2000** to **November 30, 2023**. 

## 02. BENCHMARK STRATEGY
The goal is to leverage reinforcement learning to train models (**A2C** and **PPO**) that can dynamically allocates *weights* to different assets with the goal of **maximizing** *returns* and compare the performance of the RL-based algorithms against two *benchmark* strategies: equal weights (**EW**) strategy and the mean-variance optimization (**MMVO**) strategy.

**EW**

An equal-weight strategy is a *straightforward* investment approach where each asset or security in a portfolio is assigned an **equal weight**, regardless of its individual characteristics such as market capitalization, volatility, stock price, or other factors. It involves distributing an **equal amount** of capital to each asset in the portfolio, ensuring that each asset contributes *equally* to the overall performance of the portfolio. This strategy aims to achieve *simplicity*, *diversification*, and a *uniform* exposure to each component. Once allocated an equal percentage of the total capital to each security in the portfolio, it consists of periodically **rebalancing** the portfolio to maintain equal weights which may have deviated due to price changes. 

**MMVO**

Modern Portfolio Theory (**MPT**), developed by Harry Markowitz in 1952, is based on the idea of achieving an optimal *risk-return* **trade-off** by combining assets in a portfolio. It emphasizes the importance of *diversification* and aims to **maximize** the expected *return* of a portfolio for a given level of risk or **minimize** the *risk* for a target level of expected return. This strategy involves calculating the expected *returns*, *variances*, and *covariances* of assets to construct an **efficient frontier** of portfolios: the *optimal* portfolio is then selected based on the investor's **risk tolerance** and return expectations.

## 03. RL ALGORITHMS
In order to **outperform** the *benchmark* strategies, we decided to use reinforcement learning-based models, including **Actor Critic** and Proximal Policy Optimization (**PPO**). 

**A2C**

The model combines elements of both **value-based** and **policy-based** methods, thus the RL algorithm is split in two parts:
- The **Actor** *(policy based)* is responsible for learning the **optimal** *policy*, which defines the agent’s strategy for selecting actions in a given state. Its goal is to **maximize** the expected cumulative *reward* by adjusting its policy (ex. Policy Gradients).
- The **Critic** (value based) is responsible for learning the **value** *function*, which estimates the expected cumulative *reward* for a given state. It produces the **Q values** of the action, so evaluates the action by computing the value function (ex. Q learning).
The objective function combines the policy gradient and the advantage function to maximize the expected cumulative reward. The result is that the *overall* architecture will learn more **efficiently** than the two methods separately.

**PPO**

It is a *policy optimization* method for decision-making in a given environment that aims to improve the policy while ensuring *stable* and *efficient* learning. The algorithm aims to *iteratively* **update** the policy to **maximize** cumulative *rewards* over time. PPO addresses the **trade-off** between exploration and exploitation, encouraging the agent to explore new strategies while maintaining a level of stability in the learning process: *exploration* involves trying new actions to discover their effects, while *exploration* concerns favoring known actions to yield high rewards. 

## 04. MODEL COMPARISON
Inspecting the cumulative returns of different strategies across years, we can infer that the **RL** algorithms **outperformed** the Equal-Weights strategy. Being more precise, in various periods RL-based portfolio optimization models **outperformed** all benchmark strategies (including MVVO).
Therefore, the **MMVO** strategy **outperforms** the others across multiple key perfomance metrics, demostrating superior *risk-adjusted* returns, *downside protection*, overall *profitability* and *resilience*, reaching a cumulative return of **50.95%** and a CAGR of **6.16%**.

Even if Reinforcement Learning algorithms outperfomed the MMVO strategy only in **DD days**, we can conclude that RL-based portfolio optimization models may be able to outperform the EW strategy. In particular:
- **RL's Promise in Portfolio Optimization**:
Demonstrates potential in *adapting* to market changes and *maximizing* returns.
- **Current Limitations**:
Does not include *transaction* costs, which may affect real-world applicability.
- **Expanding Data Sources**:
Utilize company reports, social media, news, and macroeconomic factors for more *informed* and *improved* predictions.
