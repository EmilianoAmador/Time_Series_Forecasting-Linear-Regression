# A Yen for the Future: Time Series Analysis and Linear Regression of the Japanese Yen Against the USD
![Yen Photo](Images/unit-10-readme-photo.png)
<br/>
It's 2020, many companies have globalized and continue to do so every day. However, being global comes with the extra homework of dealing with the exchange rates of foreign currencies. To understand the behavior of these fluctuating currencies, the financial department must develop techniques that will increase the company's predictive accuracy while doing international business. 
<br/>
The demand for accurate tools that forecast exchange rate behavior is large. Even local trading firms such as hedge funds are highly interested in anything that will give them a consistent upper-hand in predicting currency movements. 
<br/>
To better understand foreign currency behavior, I used Japanese Yen vs. USD Futures data to create two forecasting models: time series forecasting and linear regression forecasting. The time series forecasting technique splits the data into various trends and analyzes each individually. The linear regression model uses algorithms to predict Yen futures ("settle") returns. Lastly, I examined the accuracy of the models and whether they could help in understanding the future direction of these currencies.
<br/>
![](Images/Historic_values.gif)
<br/>
<br/>
<br/>
<br/>
<br/>
**Summary of techniques used:**
## Time Series Forecasting

### 1. Decomposition Using a Hodrick-Prescott Filter
Using a Hodrick-Prescott Filter, we can remove the cyclical components of the daily Settle price to obtain a smooth trend representation of this data. This version of the time series becomes more sensitive to long term than short term fluctuations.
<br/>
In the graph below, we can view the smooth trend (orange) against the actual price (blue), which reveals tradable opportunities. If the blue falls below the orange, then we can conclude that the Yen is undervalued; and, therefore, can serve as a short-term buying opportunity.
![](Images/SettleVSTrend.png)

Similar to the Trend, the noise also reveals buying and selling opportunities. Values above zero indicate to sell, while values below zero indicate to buy.
![](Images/Noise.png)

### 2. ARMA 
This forecasting model makes future value predictions based on the stationary data of the settle prices. We used the yen's daily percent change in order to make a non-stationary data such as the Settle price of the Yen into stationary (daily percent change). The Graph below demonstrates a 5-day future prediction of the daily percent change of the Yen vs USD.

![](Images/ARMA2.png)
![](Images/ARMA.png)

### 3. ARIMA
This forecasting model predicts the future values of the Yen's Settle price for the next 5 days. Unlike the ARMA, the ARIMA allows for non-stationary values to be used. In this case we used the actual settle price of the Yen.

![](Images/ARIMA2.png)
![](Images/ARIMA.png)

### 4. GARCH
GARCH allows us to predict the volatility associated with the future values of the Yen. The Graph below demonstrates that the volatility of the Yen against the USD will increase within the next 5 days. This can be due to the drastic fluctuations of price throughout the years.

![](Images/GARCH2.png)
![](Images/GARCH.png)

#### Conclusion For Time Series Analysis:
Based on your time series analysis, would you buy the yen now?
Is the risk of the yen expected to increase or decrease?
Based on the model evaluation, would you feel confident in using these models for trading?

Based on the model evaluation, I would not feel confident in using these models for trading yet. Other metrics must be evaluated before making final decisions. The weak p-values that the ARMA and ARIMA models yield indicate that the model requires further investigation before it can be used for trading. If the model had better statistical performance based on this data alone, then I would certainly not buy the yen will depreciate in the next 5 days.

### Linear Regression
This forecasting model takes the lagged returns of the Yen's settle price (training data) and makes predictions based on this information (testing data). Using the RMSE we were able to compare its performance.

![](Images/Linear_regression.png)

Upon assessing this model with the square root mean sample error (RMSE) it is evident that it performs best with the out-of-sample data (data it has not seen before) yielding an RMSE of .4152, while the RMSE in the in-sample data (or training data) yielded .5658 upon calculation. This lower value for the out-of-sample indicates that testing data has a looser fit to the regression line than that of training data. Typically, the out-of-sample RMSE is higher than the training RMSE, but in this case it is the other way around.
