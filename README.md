### Developed by : M.Pranathi
### Register no : 212222240064
# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### Date: 
### AIM:
To Illustrates how to perform time series analysis and decomposition on supermarketsales.
### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:
```
# Step 1: Import the required packages
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

# Step 2: Read the data using pandas (replace this with the path to your actual dataset)
df=pd.read_csv('supermarketsales.csv')
df.head()


# Step 3: Convert 'Date' column to datetime format
df['Date'] = pd.to_datetime(df['Date'])

# Set 'Date' as the index
df.set_index('Date', inplace=True)

# Step 4: Aggregate the data daily for the 'Total' column
df_daily = df.resample('D').sum()

# Perform seasonal decomposition on the 'Total' column (additive model and weekly period assumption)
result = seasonal_decompose(df_daily['Total'], model='additive', period=7)

# Step 5: Plot the decomposed components
fig = result.plot()
plt.tight_layout()

# Step 6: Display the decomposed results
plt.show()

# Print the results (Trend, Seasonal, Residuals)
print("Trend Component:\n", result.trend.dropna().head())
print("\nSeasonal Component:\n", result.seasonal.dropna().head())
print("\nResidual Component:\n", result.resid.dropna().head())



```

### OUTPUT:
FIRST FIVE ROWS:

![image](https://github.com/user-attachments/assets/9f13187b-2108-4afb-abec-3c3d5b30d3d4)


PLOTTING THE DATA:

SEASONAL PLOT REPRESENTATION :

![image](https://github.com/user-attachments/assets/ad9e1eac-6120-4e69-9702-f7172d3b3af5)

TREND PLOT REPRESENTATION :

![image](https://github.com/user-attachments/assets/22524267-bd09-486c-9b70-728e038f14d7)

OVERAL REPRESENTATION:

![image](https://github.com/user-attachments/assets/f6b23382-f7b6-476b-9fa4-0b207bbf3cda)


### RESULT:
Thus we have created the python code for the time series analysis and decomposition.
