# Stock Price Prediction Using RNNs
## Objective
The objective of this assignment is to try and predict the stock prices using historical data from four companies IBM (IBM), Google (GOOGL), Amazon (AMZN), and Microsoft (MSFT).

We use four different companies because they belong to the same sector: Technology. Using data from all four companies may improve the performance of the model. This way, we can capture the broader market sentiment.

The problem statement for this  can be summarised as follows:

Given the stock prices of Amazon, Google, IBM, and Microsoft for a set number of days, predict the stock price of these companies after that window.

## Data Insights
You worked with stock price data for IBM, Google (GOOGL), Amazon (AMZN), and Microsoft (MSFT).

Each company's dataset contained 3019 records from Jan 1, 2006 to Jan 1, 2018.

Features included: Open, High, Low, Close, Volume.

You combined all four datasets into one master DataFrame with appropriately renamed columns.

Missing values were handled carefully.

Heatmap analysis showed strong correlations between Open, High, Low, and Close prices (as expected).

Google is highly correlated with Amazon and Microsoft with a correlation of 0.97 .

Amazon and Microsoft are also highly correlated with correlation of 0.95

A 21-day sliding window was chosen for modeling (based on the autocorrelation plot).

## Data Preprocessing
Datasets are loaded and combined them into one master DataFrame.

Append the stock names into the columns of their respective data frame.

Missing values were handled carefully.

Created windows from the master data frame and obtain windowed X and corresponding windowed y values.

Scaled the data sets in an appropriate manner.

Data was split into training(80%) and Test(20%) sets.

## Model Building
Five RNN models were built with the following architecture:

### Model 1(Simple RNN):

1 Simple RNN layer
1 Dropout layers to prevent overfitting
Learning rate to control the speed of learning dimensions
x activation for classification
### Model 2(LSTM -basic):

1 LSTM layer
1 Dropout layers to prevent overfitting
Learning rate to control the speed of learning
Dense layer for classification
### Model 3(Improved LSTM):

2 LSTM layers
2 Dropout layers to prevent overfitting
Learning rate to control the speed of learning *Dense layer for classification
### Model 4(GRU):

2 GRU layers
2 Dropout layers to prevent overfitting
Learning rate to control the speed of learning *Dense layer for classificationcation
### Model 5(Bidirectional LSTM):

2 Bidirectional simple RNN layers
2 Dropout layers to prevent overfitting
Learning rate to control the speed of learning
Dense layer for classification
## Compilation:
Optimizer: Adam

Loss Function: mean squared error

## Models Trained
| Model	| Test MSE | R2 score	| Comments |
| --- | --- | --- | --- |
| Simple RNN	| 0.0038 | 0.829	| Best performer! Simple but effective. |
| LSTM (basic)	| 0.0052	| 0.75	| Better than remaining models, but still worse than Simple RNN |
| Improved LSTM |	0.0436 |	-1.33 |	Worse than basic LSTM, maybe underfitting. |
| GRU	| 0.0417	| -0.94	| Worse than basic LSTM, maybe underfitting. |
| Bidirectional LSTM	| 0.0595	| -3.43	| Much worse! Bidirectional not suited for this series prediction. |

## Key Observations
Simple RNN surprisingly performed the best here! Likely because:
Stock market data isn't very long-term dependent.
Simple RNNs capture short-term patterns better for this task.
LSTM/GRU were heavier and probably overfit slightly.
Bidirectional LSTM was not appropriate because future information is unavailable in stock prediction.
Model complexity hurt more than helped for this dataset.
## Final Conclusion
✅ Simple RNN with a 21-day window gave the best results in this stock price forecasting task.

✅ It kept the model lightweight, fast to train, and accurate enough.

✅ More complex models (LSTM, GRU, Bi-LSTM) didn't outperform — possibly because stock prices have short-term dependencies, not deep long-term ones.
