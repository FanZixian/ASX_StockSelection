# StockSelection_ML

System:
CPU: Normal
GPU: NVIDIA, CUDA12.0, RAPIDS 23.02

Training and Validation sets: 2017.01.03 – 2019.11.05 (Totally 720 trading days when rolling starts) / 2021.04.09 (Totally 1080 trading days when rolling ends)
Test set: 2022.04.12 – 2022.09.08 (Totally 360 trading days)

Rolling window: monthly adjustment
In order to increase the amount of data during each training session, we use a rolling training model with the presence of overlappings. 
A total of 360 trading days of data are available for each training session.
For example.
First training: all data from 1 2017.01.03 to 2019.11.05 is applied to the training and then validation is performed using data from 2019.11.06 to 2019.12.17.
Second training: the window slides forward one month, i.e. all data from 2017.02.15 to 2019.12.17 are applied to the training,
and then validation is performed using data from 2019.12.18 to 2020.02.03.


Indicators generation:
# Original data:
Price, Volume, Dividends, Stock splits

# Technical fundamental data:

OpenClose_spread, Highlow_spread, 5_Days_MA, 10_Days_MA, 15_Days_MA, 30_Days_MA, 5_Days_VAR, 15_Days_VAR, 30_Days_VAR

# Technical advanced data:
15_Days_EWMA15, 15_Days_RSI, 15_Days_MFI, 15_Days_ATR, ForceIndex, Typical_MACD

# Models considered:
1. Random Forests
Parameters:
rf_n_estimators = [50, 100, 400, 800]
rf_max_depth = [50, 100, 400, 1000]
rf_max_leaves = [1000, 500, 200, 100]
rf_min_samples_split = [2, 10, 20, 50]
rf_n_bins = [32, 128, 512]
scalers = [StandardScaler(), MinMaxScaler(), QuantileTransformer()]

Parameters number (For one stock): 576
Training time (For one stock): 







