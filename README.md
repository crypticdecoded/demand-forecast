import matplotlib


print ("Hello World!")


import pandas as pd
import numpy as np 
import matplotlib.pyplot as plt

dates = pd.date_range(start='2023-01-01', periods=100, freq='D')
data = pd.Series(range(100)) + pd.Series(pd.Series(np.random.randn(100)).cumsum())
ts = pd.DataFrame({'Date': dates, 'Value': data})

ts.set_index('Date', inplace=True)

plt.figure(figsize=(10, 5))
plt.plot(ts['Value'], label='Original')
plt.title('Basic Time Series')
plt.xlabel('Date')
plt.ylabel('Value')
plt.legend()
plt.show()

ts['7-day MA'] = ts['Value'].rolling(window=7).mean()
plt.figure(figsize=(10, 5))
plt.plot(ts['Value'], label='Original')
plt.plot(ts['7-day MA'], label='7-day Moving Average', color='red')
plt.title('Time Series with 7-day Moving Average')
plt.xlabel('Date')
plt.ylabel('Value')
plt.legend()
plt.show()# demand-forecast
