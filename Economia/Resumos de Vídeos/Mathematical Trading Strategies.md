
# Mathematical Trading Strategies


![](https://i.ytimg.com/vi/mC_4Xiy9gnk/hqdefault.jpg)


## Statistical Arbitrage Trading Strategies


- The speaker, Nielson I. Guard, is a professor at the [[University of Chicago]] and the director of the Mathematical Finance Master of Science program.
- He is presenting a lecture on statistical arbitrage trading strategies, a strategy that involves exploiting price discrepancies between related assets.



## Lecture Structure


- The lecture is divided into three parts: empirical studies of stock prices, the theory behind statistical arbitrage, and open questions regarding the strategy.
- The speaker begins by showing a graph of daily [[Intel]] stock prices, which demonstrates that stock prices are volatile and unpredictable.



## Mean-Reverting Patterns


- He then shows a graph of the difference between daily stock prices, which appears to oscillate around zero, suggesting that the differences are mean-reverting.
- The speaker explains that the goal of statistical arbitrage is to identify and exploit these mean-reverting patterns in stock prices.



## Pairs Trading


- [[Pairs trade | Pairs Trading]]: Pairs trading involves finding two stocks whose prices move together in a predictable way. The goal is to create a portfolio of these two stocks that oscillates around a fixed value.
- Identifying Pairs: The speaker explains that finding pairs of stocks with a strong linear relationship is crucial. They use the example of E*TRADE Corp. and [[Goodyear Tire and Rubber Company | Goodyear Tire & Rubber Co.]], showing how their prices exhibit a linear relationship.



## Creating a Trading Strategy


- Creating a [[Trading strategy | Trading Strategy]]: Once a pair is identified, a trading strategy is developed based on the residuals (differences between the actual price and the price predicted by the regression line). The strategy involves buying the portfolio when the residual is above a certain threshold and selling it when the residual is below a threshold.
- Portfolio Construction: The speaker describes a specific portfolio for the E*TRADE and Goodyear example. It involves buying one share of Goodyear and shorting 0.57 shares of E*TRADE. This portfolio is designed to oscillate around zero.



## Trading Rules


- Trading Rules: The speaker outlines a conservative trading strategy. They suggest buying the portfolio when the price is below a green line, selling it when the price is above a red line, and exiting the position when the price is within a band around zero.
- Risk and Profitability: The speaker acknowledges that more aggressive strategies, such as shorting the portfolio at higher levels and going long at lower levels, can be more profitable but also riskier.



## Testing the Strategy


- The speaker is discussing a mathematical [[Trading strategy | trading strategy]] that involves shorting a portfolio and exiting at a certain band.
- The strategy is designed to be conservative, with no money involved in putting it on.
- The strategy is tested using historical data, which shows a profit of $20 per unit traded.



## Out-of-Sample Data


- However, the speaker acknowledges that this is not a realistic picture, as it assumes knowledge of future prices.
- To test the strategy realistically, out-of-sample data is needed. This involves calibrating the model on one dataset and then testing it on a different dataset.
- When the strategy is tested on out-of-sample data, the results are less profitable than the initial historical data test.



## Challenges in Pairs Trading


- The strategy still shows some profitability, but it experiences a significant loss at one point.
- This loss occurs because the linear relationship between the two stocks breaks down after about 30 trading days.
- The speaker suggests that the strategy should have been exited at this point and a new pair of stocks should have been sought.
- The main challenge in pair trading is identifying pairs and determining when the relationship between them breaks down, requiring an exit from the trade.



## Exit Strategies


- A simple exit strategy involves exiting the trade when the portfolio price deviates more than three standard deviations from zero. This helps limit losses by preventing the portfolio from experiencing significant drawdowns.
- The speaker uses the example of [[Long-Term Capital Management]] (LTCM) to illustrate the risks associated with mean-reverting strategies. LTCM suffered significant losses due to a prolonged deviation from the mean, leading to liquidity issues and forced liquidation.



## Risk Management


- The speaker highlights the dangers of leverage, particularly in situations like the 2010 flash crash, where rapid market movements can trigger margin calls and force liquidations at unfavorable prices.
- The speaker emphasizes the importance of the Sharpe ratio and maximum drawdown in evaluating trading strategies. A Sharpe ratio above 0.5 is considered good, while a large drawdown can lead to investor withdrawals, impacting hedge fund performance.



## Cointegration


- The speaker introduces the concept of [[Cointegration | cointegration]], discovered by [[Robert F. Engle | Robert Engle]] and [[Clive Granger]], which involves finding a linear combination of two non-stationary time series that results in a stationary time series.
- The speaker explains that cointegration can be used to identify pairs of stocks for trading by regressing them against each other and analyzing the residuals.



## Unit Root Tests


- The text discusses the concept of a "[[Unit root test | unit root test]]" in the context of stock prices. This test determines whether the residuals of a time series model form a [[Stationary process | stationary process]], meaning they oscillate around a constant mean.
- A stationary process is characterized by a coefficient (Rho) less than 1. When Rho equals 1, the process is a random walk, and when Rho is greater than 1, the process explodes.



## Dickey-Fuller and Phillips-Perron Tests


- The Dickey-Fuller test and the Phillips-Perron test are two common unit root tests. These tests calculate a test statistic that follows a specific distribution, known as the Dickey-Fuller distribution.
- The null hypothesis of these tests is that Rho equals 1. To reject this hypothesis and conclude that the process is stationary, the test statistic must be significantly far from zero.



## ARCH Process


- A major limitation of the Dickey-Fuller and Phillips-Perron tests is that they assume the error terms are independently and identically distributed ([[Independent and identically distributed random variables | i.i.d.]]), which is often not the case with stock prices.
- Stock prices often exhibit periods of high volatility followed by periods of low volatility, violating the i.i.d. assumption.
- To address this issue, the text introduces the concept of an ARCH ([[Autoregressive conditional heteroskedasticity | Autoregressive Conditional Heteroscedasticity]]) process, which models the variance of the error terms.
- The ARCH process allows for periods of high and low volatility, providing a more realistic representation of stock price behavior.
- By incorporating an ARCH process, the Dickey-Fuller test can be modified to account for the non-constant variance of the error terms.



## Study Results


- The speaker is discussing the results of a study that looked for pairs of stocks with a statistically significant relationship, using the Dickey-Fuller test.
- The study found 35 pairs of stocks out of 125,000 that had a Dickey-Fuller statistic less than -7, indicating a strong rejection of the null hypothesis of a unit root.
- However, the speaker notes that the Dickey-Fuller test can be sensitive to high volatility, and that [[American International Group | AIG]], a company that experienced significant volatility during the period studied, appeared in 31 of the 35 pairs.



## Open Questions


- After removing pairs involving AIG, the study was left with only four pairs.
- The speaker then discusses the difficulty of finding a fundamental or macroeconomic connection between the stocks in these pairs.
- The speaker acknowledges that the probability of finding a Dickey-Fuller statistic of -7 is extremely low, and that the four pairs found are unlikely to be random.
- The speaker also notes that the method used does not distinguish between positively and negatively correlated pairs, and that it is possible for stocks to have a negative correlation in their returns, even if they are both positively correlated to the market.
- The speaker concludes by stating that there are many open questions about the results of the study, and that further research is needed.



## Time Period for Finding Pairs


- The video discusses the concept of "[[Pairs trade | pairs trading]]" in mathematical trading strategies. This involves identifying pairs of stocks that move together and exploiting their price discrepancies.
- The speaker addresses the question of how long a time period is appropriate for finding these pairs. They argue that using a shorter time period, like three months, can be more effective than using longer periods like six months.



## Example of a Profitable Pair


- The speaker provides an example of a pair, [[Goldman Sachs]] and [[Constellation Energy]], that was identified using a three-month period and resulted in a profitable [[Trading strategy | trading strategy]].
- The speaker addresses concerns about the statistical significance of the results, emphasizing that the probability of finding such strong relationships by chance is extremely low.



## Assumptions and Data


- The speaker discusses the assumptions underlying the statistical tests used to identify pairs, specifically mentioning the GARCH process for modeling volatility.
- The speaker highlights the importance of using intraday data, specifically focusing on the period after the first half-hour of trading, to avoid the influence of pre-open trades.



## Real-World Application


- The speaker mentions that the strategies discussed are being actively traded with real money and have proven to be profitable.
- The speaker acknowledges that periods of high volatility, like the end of 2008, can lead to more false rejections in the statistical tests and may require adjustments to the selection process.



## Avoiding Biases


- The speaker suggests that stocks appearing in multiple pairs should be eliminated from the selection process to avoid potential biases.
- The speaker explains that pair trading strategies rely on identifying statistical relationships between the prices of different stocks.



## Market Fluctuations and Hedge Funds


- These relationships can change over time, making it difficult to determine when to exit a trade.
- The speaker mentions that hedge funds often use long-short strategies, where they create portfolios of stocks with high and low scores based on various factors.
- When hedge funds need to adjust their positions, they may buy or sell multiple stocks simultaneously, creating temporary price relationships between them.
- The speaker highlights the example of the 2008 financial crisis, where many hedge funds had similar portfolios and were forced to liquidate their positions, leading to a [[Liquidity crisis | liquidity crisis]].
- The speaker concludes that pair trading strategies can be effective for short-term trading, but they are susceptible to market fluctuations and the actions of other market participants, particularly hedge funds.







## Renaissance Technologies and High-Frequency Trading


- [[Renaissance Technologies]] is a well-known hedge fund that uses high-frequency trading strategies and employs mathematicians and computer scientists.
- The speed of light is becoming a factor in high-frequency trading, with exchanges setting up servers close to each other to gain a competitive advantage.



## Flash Crashes


- Flash crashes are events that cause sudden and significant volatility, potentially wiping out short option positions.
- The exact cause of flash crashes is unknown, but they are considered traumatic events for those holding short options.



## Technical Trading


- The speaker acknowledges that there are traders who make a living from technical trading, even though the efficient market hypothesis suggests it shouldn't be possible.



## Factoring in Market Movement


- The speaker mentions that stock prices in pairs are often correlated to the overall [[S&P 500]].
- The speaker suggests that factoring in the movement of the stock relative to the S&P 500 could be a useful strategy.
- The speaker notes that many traders have already been using this strategy, which may have reduced the opportunities available.



## Exit Algorithms and Liquidity


- The speaker emphasizes the importance of exit algorithms in this type of [[Trading strategy | trading strategy]].
- The speaker acknowledges that the amount of money that can be deployed in this strategy depends on the liquidity of the stocks involved.
- The speaker suggests that highly liquid stocks with high volume could potentially accommodate a larger amount of money without disrupting the relationship between the stocks.


