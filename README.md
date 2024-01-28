# ValueInvestor 

# Background:

Our goal is to establish a robust intelligent system to aid our value investing efforts using stock market data. We make investment decisions and based on intrinsic value of companies and do not trade on the basis of daily market volatility. Our profit realization strategy typically involves weekly, monthly and quarterly performance of stocks we buy or hold.


# Data Description:
Set of portfolio companies trading data from emerging markets including 2020 Q1-Q2-Q3-Q4 2021 Q1 stock prices.Each market's operating days varies based on the country of the company and the market the stocks are exchanged. 
Predict with 2021 Q1 data.


# Goal(s):
Predict stock price valuations on a daily, weekly and monthly basis. Recommend BUY, HOLD, SELL decisions. Maximize capital returns, minimize losses. Ideally a loss should never happen. Minimize HOLD period.
Evaluate on the basis of capital returns. Use Bollinger Bands to measure your systems effectiveness.

# Solution:


After trying different time series forecasting models for our initial dataset focused on Russia's Sberbank Stocks, LSTM model is the best fit.
![models](https://github.com/kuzhuppillil/hNFXdIqBxEtwfdV2/assets/25860818/c6eb1c5f-eeaf-45b0-ad1e-876faaceeabe)

1. **Exponential Smoothing** (MAPE: 2.69%): While Exponential Smoothing is straightforward to implement and captures general trends, its forecasting performance diminishes with intricate trends, complex patterns, or long-term dependencies. 
2. **FB Prophet** (MAPE: 16.83%): Designed to handle missing data and outliers effectively, FB Prophet can also accommodate seasonality and holidays. However, it's not most suitable choice for rapidly changing trends and complex patterns.
3. **ARIMA (AutoRegressive Integrated Moving Average)**(MAPE: 2.91%): ARIMA performs well with linear trends and stationary time series, and it can capture seasonality through differencing. But, its efficacy diminishes when faced with non-linear patterns, making it less suitable for forecasting complex trends.
4. **LSTM (Long Short-Term Memory)**(MAPE: 1.65%): LSTM stands out for its ability to capture complex, non-linear relationships and it can learn well from long sequences of data and capture temporal dependencies.

### Why LSTM is Preferred:
    Non-Linearity: Stock prices often exhibit non-linear patterns, and LSTMs are well-suited for capturing such complex relationships.
    Temporal Dependencies: LSTMs can capture long-term dependencies in time series data, which is crucial for stock price forecasting.
    Adaptability: LSTMs are capable of adapting to changing patterns over time, making them suitable for dynamic stock markets


### By utilizing LSTM for univariate timeseries forecasting in conjunction with the Bollinger Bands strategy, along with customized parameters and special conditional triggers, we have effectively met the project objectives. This approach has resulted in no losses and achieved the maximum possible return on investment.
![Dongkuk](https://github.com/kuzhuppillil/hNFXdIqBxEtwfdV2/assets/25860818/a25c6a14-6d01-4f80-b928-32fcd63e73f1)
![Impala](https://github.com/kuzhuppillil/hNFXdIqBxEtwfdV2/assets/25860818/bf2f8453-5698-4e0f-9d3e-3dfa55ed06bc)
![Koc_holding](https://github.com/kuzhuppillil/hNFXdIqBxEtwfdV2/assets/25860818/fadb0c21-0dfb-4f0e-bfdc-2f486a7792cc)
![Medinet](https://github.com/kuzhuppillil/hNFXdIqBxEtwfdV2/assets/25860818/c05c5d6e-cedc-4b80-af8f-4280ec3798e0)
![Pampa](https://github.com/kuzhuppillil/hNFXdIqBxEtwfdV2/assets/25860818/5baa2a2a-f68d-4590-9018-73a6a10bd5ec)
![Cementos](https://github.com/kuzhuppillil/hNFXdIqBxEtwfdV2/assets/25860818/0c408bec-7133-45d7-95b6-9972a127c19c)
![Sberbank](https://github.com/kuzhuppillil/hNFXdIqBxEtwfdV2/assets/25860818/044acfb2-3001-46eb-a9d4-5173a6999fe9)


## Trading strategy:

This Trading algorithm is designed to make buy, hold, and sell decisions by leveraging a Bollinger Bands strategy with the goal of maximizing capital returns, minimize losses, and decrease the holding period.

Three additional parameters provide more control over trade decisions, specific conditions are employed to assess the trend. Depending on the forecasted trend, we can adjust the thresholds inorder to ensure maximum returns and minimal losses. For example, a minimum margin parameter of 1% might be applied for a downward trend, while 8-10% could be utilized for an upward trend.

    For a buy signal, it verifies whether the previous closing price is below the lower Bollinger Band, and the current price is within a specified threshold above the lower Bollinger Band.
    For a sell signal, it examines whether the current price surpasses the upper Bollinger Band or if the maximum holding period has been reached. Additionally, it checks if the current price is above a minimum margin from the locked price. The inclusion of a Minimum margin is empoyed to enforce the maximum possible profit.
    The trailing stop feature automatically adjusts the stop-loss mark based on the current price. If the current price falls below a certain percentage of the stop-loss price, a stop-loss trigger is activated. Consequently, stocks are sold, and the available capital is updated, thus minimizing losses.

### Note: While this trading strategy should reasonably meet our objectives given the limited dataset length and samples, further fine-tuning may be necessary based on the specific dataset. Additionally, integration of supplementary indicators like the Relative Strength Indicator (RSI) and the BandWidth indicator, which complement Bollinger Bands, could be explored for further refinement.


# References:

    https://medium.com/analytics-vidhya/analysis-of-stock-price-predictions-using-lstm-models-f993faa524c4
    https://medium.com/codex/introduction-to-prophet-algorithm-a59e463a6c72
    https://medium.com/analytics-vidhya/time-series-forecasting-arima-vs-prophet-5015928e402a
    https://www.analyticsvidhya.com/blog/2023/06/sarima-model-for-forecasting-currency-exchange-rates/
    https://neptune.ai/blog/arima-sarima-real-world-time-series-forecasting-guide
    https://towardsdatascience.com/time-series-forecasting-with-arima-sarima-and-sarimax-ee61099e78f6
    https://www.investopedia.com/terms/b/bollingerbands.asp
    https://www.investopedia.com/terms/t/trailingstop.asp
    https://www.investopedia.com/terms/s/sma.asp





