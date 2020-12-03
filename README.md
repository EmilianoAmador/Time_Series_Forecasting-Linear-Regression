# A Yen for the Future:
![Yen Photo](Images/unit-10-readme-photo.png)
## Time Series Analysis and Linear Regression of the Yen Against the USD

This project evaluates the performance of various techniques applied in a time series forcasting for the historic values of the Japanese Yen (JPY) against the United States Dollar (USD). It also takes a look in evaluating the accuracy of future value predictions by using a Linear Regression of the JPY lagged returns. 

![](Images/Historic_values.gif)

Summary of techniques used:

### Decomposition Using a Hodrick-Prescott Filter
Using a Hodrick-Prescott Filter, decompose the Settle price into a trend and noise. Plotting the smooth trend (orange) against the actual price (blue) reveals tradable opportunities. If the blue line falls below the orange then we can conclude that the Yen is temporarily undervalued and therefore can serve as a short term buying opportunity.
![](Images/SettleVSTrend.png)

Similar to the Trend, the noise also reveals buying and selling opportunity. Values above zero indicates to sell, while values below zero indicate to buy.
![](Images/Noise.png)

### ARMA 
This forecasting model makes future value predictions based on the stationary data of the settle prices. We used the yen's daily percent change in order to make a non-stationary data such as the Settle price of the Yen into stationary (daily percent change). The Graph below demonstrates a 5-day future prediction of the daily percent change of the Yen vs USD.

![](Images/ARMA2.png)
![](Images/ARMA.png)

### ARIMA
This forecasting model predicts the future values of the Yen's Settle price for the next 5 days. Unlike the ARMA, the ARIMA allows for non-stationary values to be used. In this case we used the actual settle price of the Yen.

![](Images/ARIMA2.png)
![](Images/ARIMA.png)

### GARCH
GARCH allows us to predict the volatility associated with the future values of the Yen. The Graph below demonstrates that the volatility of the Yen against the USD will increase within the next 5 days. This can be due to the drastic fluctuations of price throughout the years.

![](Images/GARCH2.png)
![](Images/GARCH.png)

#### Conclusion For Time Series Analysis:
Based on your time series analysis, would you buy the yen now?
Is the risk of the yen expected to increase or decrease?
Based on the model evaluation, would you feel confident in using these models for trading?

Based on the model evaluation I would not feel confident in using these models for trading. The reasoning behind this decision is based on the poor p-values that the ARMA and ARIMA models yield. On top of this issue, the GARCH model predicts that the volatility of the yen against the dollar will increase. Therefore, I would not make a decision based on this model. If the models had better statistical performance then I would certainly buy considering that the model predicts the yen will appreciate in the next 5 days.

### Linear Regression
This forecasting model takes the lagged returns of the Yen's settle price (training data) and makes predictions based on this information (testing data). Using the RMSE we were able to compare its performance.

![](Images/Linear_regression.png)

Upon assessing this model with the square root mean sample error (RMSE) it is evident that it performs best with the out-of-sample data (data it has not seen before) yielding an RMSE of .4152, while the RMSE in the in-sample data (or training data) yielded .5658 upon calculation. This lower value for the out-of-sample indicates that testing data has a looser fit to the regression line than that of training data. Typically, the out-of-sample RMSE is higher than the training RMSE, but in this case it is the other way around.
