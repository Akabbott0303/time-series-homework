# Time Series Homework

This repository contains code, written in Python using pandas, that runs time series analysis on data to predict future differences in values of two currencies, the Japanese Yen and the US dollar.

The initial plotting of the settle price appears to show a slight increase over time, with many ups and downs over the period. There is too much noise in the graph to be able to see what is happening with the Yen price from year to year. Decomposing the data with the Hodrick-Prescott Filter produced a smoother line.  With the time period reduced to five years, one can see that settle price tends to dip at the end of every year.

I first used the ARMA (autoregressive moving average) model to predict future Yen prices based on past prices.  I stationarized the data per the requirements of the model by calculating the percent change of the Yen settle prices. The ARMA model does not appeart to be a good fit because the p-values are higher (>0.05).

I also used the ARIMA (autoregressive integrated moving average) model to predict future Yen prices.  The ARIMA model stationairzes the time series data within the model.  THe p-values are again high, so the ARIMA model does not appear to be a good fit for this dataset.

To forecast volatility of the Yen, I used a GARCH (generalized autoregressive conditional heteroskedasticity) model.  The p values of the GARCH model are low, so this model is a good fit to predict the volatility of the Japanese Yen.  

I likely would not buy the Yen based on this time series analysis.  It's too volatile for my comfort level, and my GARCH model suggests that volatility will increase over time.  I would not rely on the ARMA or ARIMA models but would use the GARCH model.

After running the ARMA, ARIMA, and GARCH models, I instantiated a linear regression model and fit it to training and testing data.  The out-of-sample (testing data) RMSE is lower than the in-sample (training data) RMSE. This could be because the testing data is for a smaller time period than the training data.  The smaller RMSE for the testing data might indicate that the linear regression model is a better fit for that data than for the training data.  Both RMSEs are hovering around 0.5, so the model is not an ideal fit.

Forecasting currency prices is tricky because there are so many factors that influence them.  The conclusion I am comfortable drawing from my analysis is that the price of the Japanese Yen is volatile over time.