## Machine Learning Approach [(00:29:37)](https://www.youtube.com/watch?v=DgU1lSdH3vM&t=1777s)


- Machine learning approaches to pairs trading are similar to time series methods, but offer a structured framework for finding suitable pairs. This approach involves three steps: dimensionality reduction to create a compact representation of assets, unsupervised learning clustering to group similar assets, and pair selection based on criteria like [[Cointegration | cointegration tests]], spread deviation, and frequency of trading opportunities.
- Several papers by Dunis and other researchers explore this approach, focusing on specific spreads like gasoline, soybean, corn, and ethanol. These papers often utilize [[Machine learning | machine learning]] models, particularly neural networks, to model the spread and generate trading signals.
- The framework typically involves filtering the forecasted spread using a symmetrical or asymmetrical filter, which considers the expected value and actual value to generate trading signals. This approach often incorporates the threshold autoregression model to adjust the trading process based on the spread's behavior.
