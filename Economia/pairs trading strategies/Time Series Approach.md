## Time Series Approach [(00:21:18)](https://www.youtube.com/watch?v=DgU1lSdH3vM&t=1278s)


- The time series approach to [[Pairs trade | pairs trading]] is still under development, but it offers promising potential. The Kalman filter, a key component of this approach, will be discussed in detail in a future video.
- The core idea behind the time series approach is to model the spread between two assets as a state space model. This model's parameters can be estimated using the Kalman filter. The approach then forecasts the spread's future value and applies filters to generate trading signals.
- There are various types of filters that can be used, ranging from simple threshold filters to more complex methods like adding and fernstein will and back. The choice of filter depends on the specific [[Trading strategy | trading strategy]] and desired level of complexity. The text also mentions a textbook by Sarmanto and Horta, which presents a versatile approach that combines forecasting algorithms with quantile-based signal generation. This method allows for adjusting the sensitivity of the trading signals by changing the quantile threshold.
