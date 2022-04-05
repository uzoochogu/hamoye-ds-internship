## Measurement of Electricity Prices of a District given the total amount of Electricity using time series forecasting

We’ll explore and build time series forecasting models for measurements of electricity prices  of a District given the total amount of Electricity consumed in that District from 2010 to 2021.

### Data Set Information:

The archive contains 92,016 measurements of electricity data gathered between September 2010 and February 2021.

[Dataset](https://github.com/HamoyeHQ/HDSC-Time-series-analysis-and-forecast)

### Notes:

1. The dataset is sampled on an hourly basis. It has the following features:

Attribute Information:

FullDate: Date in format yyyy-mm-dd  hh:mm:ss
ElecPrice: Prices of electricity charged in Kw per hour
Gas Price: power generated was done via a gas power plant, gas price is the price of gas at time-T
SysLoad: Total Load on system or Power consumed at time-T 
Tmax: maximum temperature at time-T

### Given Instructions
1. Using the daily sampling rate (sum), divide the data into a train and test set. The first 2757 days is your train set and the last (x-2757) days is your test set. Where x is the length of the dataset. Use Facebook Prophet to train a Univariate time series model using the FullDate column as (‘dt’ or ‘ds’) and ElecPrice as ( ‘y’)

2. Multivariate Time Series Forecasting with Facebook Prophet
In the last exercise, we used only the dependent variable (ElecPrice) and the time component for our modeling (ds vs y). Next, we will build a time series model using the other variables. These variables will be added to the forecast model as a regressor on Facebook Prophet. So the 3 independent variables [‘SysLoad’,’Tmax’,’GasPrice’'] will be [‘add1’, ‘add2’, ‘add3’’] as the regressors. Split the data into train and test as done above and build a multivariate forecast model to forecast the last x-2757 days of ElecPrice.

