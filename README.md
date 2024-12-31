# Store Item Demand Forecasting

## Questions
You are given 5 years historical sales data from 50 different items at 10 different stores. Explore the dataset and answer the following questions:
1. How is the sales trend and growth rate over the 5 years?
2. How is the sales trend by different stores?
3. How is the sales trend by different items?
4. Do you have any recommendations for the growth of the stores?
5. Bonus: predict 3 months of sales for these 50 different items at 10 stores.

## Dataset
The `train.csv` contains 4 columns:
- `date`: Date of the sale data. There are no holiday effects or store closures.
- `store`: Store ID
- `item`: Item ID
- `sales`: Number of items sold at a particular store on a particular date.

The `test.csv` contains the test data that we need to predict.

## Main Finding

**Sales Trend over Month**

![image](https://github.com/user-attachments/assets/c577a97d-9cad-4efa-b93f-3396a905984e)



- From the plot, we can see the sales trend is always growing over the 5 years and grows fastest during 2013 to 2014

![image](https://github.com/user-attachments/assets/c34cabfe-fed2-4562-baae-dc8ece05870e)


- From the plot, we can see the sales is always highest of the year at July, which may caused by summer vacation. In addition, during November, there is a small peak caused by Thanks' Giving Day.
- The time-series has seasonality pattern, such as sales are always low at the beginning of the year and high at the middle(festive season maybe) of the year and again low at the end of the year. 

**Growth Rate**

![image](https://github.com/user-attachments/assets/38b8a371-a991-4c37-8fbb-6aa598ae558c)



![image](https://github.com/user-attachments/assets/7eee3587-1aa2-4e1b-b1b1-999d7a3b935a)



**Sales Trend by Store**

![image](https://github.com/user-attachments/assets/f4f68d22-d521-419f-b77e-02067eaaea95)

![image](https://github.com/user-attachments/assets/70b7c610-8d90-4ddb-b3b9-4a75f0a23ecf)



## Model

**1. Determining Stationarity**

![image](https://github.com/user-attachments/assets/285b1616-5bc2-46ad-aa5b-02e9f7500951)

- The plot clearly shows that the sales is unstable, along with its obvious seasonality.

![image](https://github.com/user-attachments/assets/38d230bf-c22d-4913-bee4-65ccf5fe1d3b)

**2. Model**

2.1 Linear Regression

![image](https://github.com/user-attachments/assets/ed659a01-3727-4ac1-b85a-08d710851f14)


2.2 LSTM

![image](https://github.com/user-attachments/assets/711f27d1-a29c-4ed4-8e61-0f701f952bad)


2.3 ARIMA Model

- We are going to apply one of the most commonly used method for time-series forecasting, known as ARIMA, which stands for Autoregressive Integrated Moving Average.
- ARIMA models are denoted with the notation ARIMA(p, d, q). These three parameters account for seasonality, trend, and noise in data.
- AR: Auto-Regressive (p): AR terms are just lags of dependent variable. For example lets say p is 3, we will use x(t-1), x(t-2) and x(t-3) to predict x(t)
- I: Integrated (d): These are the number of nonseasonal differences.
- MA: Moving Averages (q): MA terms are lagged forecast errors in prediction equation.

![image](https://github.com/user-attachments/assets/dbaa7081-6696-4e6f-9e5a-425224858ae0)


**3. Model Compare**

![image](https://github.com/user-attachments/assets/a53b4469-590d-45ee-96eb-dbeed6fe676b)

