NOTE:

# CONTEXT 
Project : replacing traditional mathematical/statistical models (like ARIMA, GARCH, or queueing theory equations) with a machine learning time-series forecasting model to predict network degradation (lag, jitter, and packet loss before a connection breaks), 

1. TECH STACK : 
  i.Java cli app  ( backend && networking ( { assignee} ))
  {
    Your core application engine handles high-throughput network monitoring and inference execution using advanced Java (NIO, Direct Buffers, and the ONNX Java Runtime).
  }

  ii. Main Prediction engine logic ml ( 75% of the app )  ( python | ml )

2. The 75% Weight : The complexity lies entirely in feature engineering, rolling-horizon sequence modeling, and evaluating forecast accuracy metrics (like RMSE and MAE) against mathematical baselines.


<!--# TESTING

1. Its very important for any new feature to pass the previous tests and the current newly added tests.
2. There should be tests for each feature.
3. The Tests are to be ran and tested manually rather than breaking the working flow.
4. The test suite / pipeline itself should be robust and fast.
5. Proper -->