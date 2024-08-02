Resumo de [[Econometria]]
feito com [recall AI](https://www.getrecall.ai/)

# Introduction [(00:00:00)](https://www.youtube.com/watch?v=g-qvFjvyqcs&t=0s)

- Max Margenot introduces himself as a data scientist at Tekton Peon and explains that he will be discussing statistical arbitrage and some fundamental statistical concepts.

- Tekton Peon is a company that aims to democratize quantitative finance by providing free open-source tools for people to research and develop algorithmic trading strategies.

- Algorithmic trading involves using instructions that terminate in finite time for the purpose of trading.

- Statistical arbitrage is a strategy that exploits inefficiencies found through statistical analysis.

- A Pairs trade is one of the most basic unit strategies of statistical arbitrage and is based on fundamental statistical concepts.

- Pairs trading involves identifying two assets that have historically moved together but are currently trading at different prices.

- The idea is to buy the undervalued asset and sell the overvalued asset, profiting from the expected mean reversion of the prices.

- Pairs trading can be used with stocks, commodities, currencies, or any other tradable asset.

- Cointegration is a statistical concept that describes the relationship between two or more non-stationary time series that move together in the long run.

- In pairs trading, cointegration is used to identify pairs of assets that have a stable long-term relationship, making them suitable for pairs trading.

- Cointegration can be tested using various statistical methods, such as the Engle-Granger test or the Johansen test.

- Stationarity is a statistical concept that describes a time series whose statistical properties are constant over time.

- A stationary time series has a constant mean, variance, and autocorrelation.

- Non-stationary time series can be made stationary through differencing or other transformations.

- Mean reversion is a statistical concept that describes the tendency of a time series to return to its long-term average after a period of deviation.

- In pairs trading, mean reversion is the expected behavior of the prices of cointegrated assets, which tend to move back towards their long-term equilibrium.

- Pairs trades are typically entered when the prices of the two assets deviate significantly from their historical relationship, and are closed when the prices mean revert.

## Stationarity [(00:04:28)](https://www.youtube.com/watch?v=g-qvFjvyqcs&t=268s)

- A stationary time series has the same parameters across time.

- A stationary time series is drawn from the same probability distribution with the same parameters.

- A stationary time series has no trend in the mean or standard deviation.

- A stationary time series looks like white noise.

## Stationary time series [(00:06:10)](https://www.youtube.com/watch?v=g-qvFjvyqcs&t=370s)

- A stationary time series is generated from a normal distribution with a mean of 0 and a standard deviation of 1.

- A stationary time series looks like white noise.

## Nonstationary time series [(00:07:03)](https://www.youtube.com/watch?v=g-qvFjvyqcs&t=423s)

- A nonstationary time series has a trend in the mean.

- A nonstationary time series is not suitable for simple descriptive statistics.

## The importance of stationarity [(00:07:25)](https://www.youtube.com/watch?v=g-qvFjvyqcs&t=445s)

- Stationarity is important for descriptive statistics and time series models.

- Many time series models assume stationarity.

- Violating the assumption of stationarity can lead to model breakdown.

## Checking for stationarity [(00:09:11)](https://www.youtube.com/watch?v=g-qvFjvyqcs&t=551s)

- The augmented Dickey-Fuller test is used to check for stationarity.

- The test confirms that the deliberately generated stationary time series is stationary and the pathological example is non-stationary.

- In the real world, the data generating process is unknown, so we rely on samples to estimate models.

- If the exact relationship of the data were known, there would be no need for model estimation.

## Hypothesis tests [(00:10:45)](https://www.youtube.com/watch?v=g-qvFjvyqcs&t=645s)

- Hypothesis tests are used to model probability distributions and make judgments based on cutoff values.

- A p-value of 0.01 indicates a 1% chance of a false positive.

- Over multiple tests, some false positives are expected, especially with subtle relationships.

- P-values are used for definitive tests, with a cutoff value determining whether to reject or fail to reject a null hypothesis.

- The augmented Dickey-Fuller test looks for a unit root in the time series and can detect trends in the standard deviation, skewness, and kurtosis.

## Don't trust graphs [(00:14:46)](https://www.youtube.com/watch?v=g-qvFjvyqcs&t=886s)

- Graphs can be misleading when looking for statistical properties.

- A time series that appears stationary on a graph may not actually be stationary.

## Testing stationarity [(00:15:12)](https://www.youtube.com/watch?v=g-qvFjvyqcs&t=912s)

- Hypothesis tests can give false positives, even for time series that appear stationary on a graph.

- Limitations exist in modeling and testing, and there is always a chance of false positives or errors.

## Cointegration [(00:15:59)](https://www.youtube.com/watch?v=g-qvFjvyqcs&t=959s)

- A stationary time series is generally mean-reverting, but a mean-reverting time series is not always stationary.

- A stationary time series can be represented as a stationary component, a deterministic component, and a random component.

## Integration of Order Zero [(00:18:01)](https://www.youtube.com/watch?v=g-qvFjvyqcs&t=1081s)

- A stationary time series has a constant mean and variance over time.

- Integration of order zero means that a time series is stationary, while integration of order one means that a time series is the cumulative sum of a stationary time series.

- In finance, returns are often assumed to be normally distributed and stationary, but this assumption should be tested.

- To break down a time series from a higher order of integration to order zero, we can take first-order differences.

- Price series are theoretically integrated of order one because they are the cumulative sum of returns.

- Statistical arbitrage involves exploiting price discrepancies between related assets, and cointegration is a concept used to identify pairs of assets that move together in a predictable way.

- Stationarity is a theoretical assumption that is not always observed in real-world data, and returns can be non-stationary, exhibiting trends or increasing volatility over time.

## Definition of Cointegration [(00:26:11)](https://www.youtube.com/watch?v=g-qvFjvyqcs&t=1571s)

- Cointegration occurs when a linear combination of integrated time series results in a stationary time series.

- Finding cointegrated time series is challenging due to the difficulty of identifying stationary time series.

- A reasonable economic basis is necessary to explore potential cointegrated relationships between price series.

## Stationary Spreads [(00:28:15)](https://www.youtube.com/watch?v=g-qvFjvyqcs&t=1695s)

- A stationary spread can be created by buying and shorting different quantities of two cointegrated price series.

- The mean and standard deviation of a stationary spread can be used to make bets on whether it will revert to the mean.

- Other metrics, such as the Hurst exponent or an Ornstein-Uhlenbeck process, can provide a time notion of when a spread is likely to revert.

## Simulation [(00:30:12)](https://www.youtube.com/watch?v=g-qvFjvyqcs&t=1812s)

- Simulated data is generated to demonstrate cointegration.

- x1 is generated from a normal distribution, and x2 is generated as x1 plus noise.

- The spread between x2 and x1 is calculated, and it is stationary and looks like white noise.

- In real financial data, it is unlikely to have perfect cointegration, so a method is needed to estimate it.

## Linear Regression [(00:32:53)](https://www.youtube.com/watch?v=g-qvFjvyqcs&t=1973s)

- Linear regression is used to estimate the relationship between the returns of two cointegrated stocks.

- The returns of one stock are expressed as a function of the returns of the other stock, with some difference between them.

- The beta value represents the exposure of one stock to the other, and the alpha value represents the unexplained return relative to the market.

- The goal is to find the beta value so that the spread between the two stocks can be calculated and traded.

## Example [(00:34:34)](https://www.youtube.com/watch?v=g-qvFjvyqcs&t=2074s)

- Pairs trading involves identifying cointegrated pairs of securities within the same sector and exploiting deviations from this relationship for profit.

- A linear regression is used to determine the beta value and construct a spread between the two securities, which is tested for stationarity to ensure a stable relationship over time.

- Statistical arbitrage involves making bets based on the assumption that prices will revert to their mean and constructing a portfolio of many such pairs, hedging market risk by taking opposite positions in each pair.

- The goal is to generate consistent returns by capturing the spread between the cointegrated pairs while minimizing risk through diversification.

## Data [(00:49:32)](https://www.youtube.com/watch?v=g-qvFjvyqcs&t=2972s)

- The most granular data available is minute level.

- Tick level or intra minute data is not available.

- Data is used for algorithmic trading, not necessarily high frequency trading.

- Data is simulated as if it was real time for live trading and backtesting.

- Assumptions for linear regressions in pairs trading include heteroscedasticity and stationarity.

- Cointegration is a stronger condition than correlation for pairs trading.

- Cointegration implies stationarity, while correlation does not.

- Correlation alone is not sufficient for determining bet sizes.

- Mean and standard deviation of the spread can be used to construct bet sizes.

- Correlation does not provide a systematic way to determine bet sizes.