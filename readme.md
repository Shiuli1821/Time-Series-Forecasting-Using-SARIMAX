# Time Series Forecasting on Furniture Sales using SARIMAX
## Table of Contents
- [Overview](#Overview)
- [Problem Statement](#Problem-Statement)
- [Methodology](#Methodology)
- [Technology used](#Technology-Used)
- [Conclusion](#Conclusion)


## Overview
Demand forecasting is one of the most important factor that is highlighted in any organizational and
enterprise level. By predicting the future demand, the company can prepare several strategic, operational and
planning decisions in order to reduce the waste of outcome. For example, the sales forecasting helps the retail
business to manage their production, purchasing, transportation and labor force. The more accurate
forecasting also can minimize the bullwhip effects in supply chain.

## Problem Statement
The dataset consists of daily sales data of various products at a superstore.Apply Time Series analysis to predict and forecast the sales of furniture
for the next month.

## Methodology
1) Read in the data using pandas.read_csv() and perform a brief EDA.
2) No missing values were found in the dataset.
3) The data contained 21 columns in total out of which only 'Order date' and 'Sales' columns were relevant. Rest of the columns were dropped.
4) The string column 'Order date' was converted to datetime in order to perform aggregate analysis like min,max,sum,etc.
5) Sales on the same date were added to using groupby function. The date column now only contained unique values.
6) The modified date column was set as index to ease plotting values against time.
7) Sales in a particular month were grouped using mean to get a single data point in a month.
8) Date vs Sales plotting cleary showed some patterns.
9) The model was check was unit root to find stationarity of the data using adfuller. The adfuller showed a unit root indicating the data is stationary.
10) The data was decomposed in seasonal,trend and residual data using seasonal_decompose.The seasonal graph showed the data repeating after 12 months.
11) A matrix was created with columns as p(number of autoregressive terms),d(number of nonseasonal differences),q(number of lagged forecast) 
    for the sarimax model to iterate over. Seasonal Factor was selected as 12 every iteration since data showed seasonality every 12 months.
12) Sarimax models were run on each row of the matrix with evaluation metric as AIC printed in output.
13) The best model was selected which showed least AIC value. 
14) The model was validated on validation data by plotting overlapping actual and predicted values.
15) This model was then used to forecast values for the next month along with confidence interval.

## Technology Used
- Jupyter Notebook
- Python

## Conclusion
The model indicated that sales is low at the beginning which increases gradually throughout the year and then decreases again at year end.

