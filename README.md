# FinRL_Contest_Starter_Kit
This repository contains the starter kit and resources for the ACM ICAIF 2023 FinRL Contest.

## Outline
  - [Task 1 Data Centric Stock Trading Starter Kit](#task-1-data-centric-stock-trading-starter-kit)
  - [Task 2 Real Time Order Execution Starter Kit](#task-2-real-time-order-execution-starter-kit)

## Task 1 Data Centric Stock Trading Starter Kit
Please download task-1-stock-trading-starter-kit.zip. To utilize FinRL library, please install required packages first:
```
pip install swig
pip install box2d
pip install git+https://github.com/AI4Finance-Foundation/FinRL.git
```
### Data
We provide the OHLCV data for 29 stocks from Jul 1, 2010 to Oct 24, 2023, for a total of 97208 pieces of data. 

The OHLCV data corresponds to Open, High, Low, Close, and Volume data, which contain most of numerical information of a stock in time series and can help traders get further judgement and predictions such as the momentum, people's interest, market trends, etc.

### Environment and Model
After data processing, contestants need to specify the state space, action space, and reward functions in the environment. The initial amount of capital is $1 million.

In the starter kit,
* The state space includes the remaining balance, the prices of all stocks, feature vectors, and the share holdings.
*	The action space includes buying, selling, and holding stocks.
*	The reward space is the change of total asset values

Since this task is data-centric, the same model design is required for a fair comparison. Specifically, teams are asked to use the PPO algorithm in the FinRL library with tunable hyperparameters.

### Performance Metrics
The performance can be measured from three dimensions:
1. Portfolio cumulative return. It measures the excess returns.
$$\text{Portfolio cumulative return} = \frac{{\text{current portfolio value} - \text{initial portfolio value}}}{\text{current portfolio value}}$$

3. Sharpe ratio. It takes into account both the returns of the portfolio and the level of risk.
$$\text{Sharpe ratio} = \frac{\text{portfolio return} - \text{riskfree rate}}{\text{standard deviation of portfolio's excess return}}$$

4. Max drawdown. It is the portfolio’s largest percentage drop from a peak to a trough in a certain time period, which provides a measure of downside risk.
$$\text{Max Drawdown }= \frac{\text{peak value} - \text{trough value}}{\text{peak value}}$$

Contestants can also compare their returns with other investment strategies or indices over a time period, such as Mean-Variance Optimization strategy and Dow Jones Industrial Average (DJIA) index.

### Feature Engineering
Since this is a data-centric task, contestants are free to design data processing strategies and perform feature engineering. In the dataset, we also provide 10 fundamental trading indicators, which are explained below. Their use is optional based on contestants’ preference. Contestants can also construct new indicators based on existing and/or external market data.

| Indicator | Name | Description |
| ----------- |---- |----------- |
| macd | Moving Average Convergence Divergence | A trend-following momentum indicator that shows the relationship between two exponential moving averages (EMAs) of a stock’s price. Traders use the MACD to identify potential trend changes, divergence between price and momentum, and overbought or oversold conditions.|
| boll_ub |Bollinger Bands Upper Band|Bollinger Bands are used to visualize the volatility and potential price levels of a stock. The upper band represents the upper volatility boundary, showing where the price might find resistance.|
| boll_lb |Bollinger Bands Lower Band|Similarly, the lower band represents the lower volatility boundary and shows where the price might find support.|
| rsi_30 |Relative Strength Index for 30 periods|A momentum oscillator that measures the speed and change of price movements. RSI oscillates between zero and 100.|
| cci_30 |Commodity Channel Index for 30 periods|A versatile indicator that can be used to identify a new trend or warn of extreme conditions. It measures the current price level relative to an average price level over a given period of time.|
| dx_30 |Directional Movement Index for 30 periods|An indicator that assesses the strength and direction of a trend of a stock. It does this by comparing highs and lows over time.|
| close_30 |30-Period Simple Moving Average of Closing Prices|Represents the average closing price over the last 30 periods. This moving average provides a smoothed representation of the asset's price over the 30 periods, making it easier to identify trends and potential support/resistance levels.|
| close_60 |60-Period Simple Moving Average of Closing Prices|Represents the average closing price over the last 60 periods. This moving average provides a smoothed representation of the asset's price over the 60 periods, making it easier to identify trends and potential support/resistance levels.|
| vix |Volatility Index|Often referred to as the "fear index", it represents the market's expectation of 30-day forward-looking volatility. It is calculated from the prices of selected stock option contracts on the S&P 500 Index.|
| turbulance |Turbulence|To control the risk in a worst-case scenario, such as financial crisis of 2007–2008, FinRL employs the financial turbulence index that measures extreme asset price fluctuation.|


## Task 2 Real Time Order Execution Starter Kit
Please download the task-2-order-execution-template.py or download it from our [submission platform](https://finrl-contest-2023.web.app/).

### Template
Contestants need to complete the Strategy class to implement order execution strategy and interact with our exchange. The functions in this class are explained below. Contestants are free to add new functions to the class but should not change the signatures of the provided functions.
* **place_market_order** allows you to place orders for the exchange at a given price/quantity, and you can call this in any function (including __init__). 
* **on_orderbook_update** is called when a new order is placed by another algorithm (BUY or SELL). 
*	**on_trade_update** is called when two orders match (one BUY, one SELL). This could be your order or two other orders. 
*	**on_account_update** is called when one of *your* orders matches with another order.

### Requirements
*	The initial capital is $100,000. 
*	The libraries that can be used include numpy, pandas, scipy, polars, and scikit-learn.
*	The submission will tested automatically on our website. You can click the submission to view the error if any function fails to run.
*	Only the most recent submission that passes linting will be used for final evaluation.

## Resources
Useful materials and resources for contestants to learn about FinRL:
* [FinRL Stock Trading Demo](https://colab.research.google.com/drive/1OuItFmsY8gSDBtQYc3N5X1SD1UjHBQ9b?usp=sharing)
* [FinRL](https://github.com/AI4Finance-Foundation/FinRL)
* [FinRL-Meta](https://github.com/AI4Finance-Foundation/FinRL-Meta)
* [FinRL Tutorials](https://github.com/AI4Finance-Foundation/FinRL-Tutorials)

