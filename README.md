### Developed By: VINOD KUMAR S
### Reg. NO . 212222240116
### Date: 

# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION


### AIM:

To Illustrates how to perform time series analysis and decomposition on the Coffee Sales data.

### ALGORITHM:

1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:

```py
import pandas as pd
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

# Load the Coffee Sales Data (make sure the path is correct)
data = pd.read_csv('coffeesalesnew1.csv')

# Convert 'Date' column to datetime format
data['Date'] = pd.to_datetime(data['Date'])

# Set the 'Date' column as the index
data.set_index('Date', inplace=True)

# Aggregate sales (e.g., monthly total sales)
data_resampled = data['CoffeeSales'].resample('M').sum()

# Display the first few rows
print(data_resampled.head())

period = 12 # Adjust based on your data availability
if len(data_resampled) >= 2 * period:
    result = seasonal_decompose(data_resampled, model='multiplicative', period=period)

    # Plot the components
    plt.figure(figsize=(12, 8))
    plt.subplot(4, 1, 1)
    plt.plot(data_resampled, label='Original', color='blue')
    plt.title('Original Time Series')
    plt.legend()

    plt.subplot(4, 1, 2)
    plt.plot(result.trend, label='Trend', color='yellow')
    plt.title('Trend Component')
    plt.legend()

    plt.subplot(4, 1, 3)
    plt.plot(result.seasonal, label='Seasonal', color='green')
    plt.title('Seasonal Component')
    plt.legend()

    plt.subplot(4, 1, 4)
    plt.plot(result.resid, label='Residual', color='red')
    plt.title('Residual Component')
    plt.legend()

    plt.tight_layout()
    plt.show()

```


### OUTPUT:

#### FIRST FIVE ROWS:
![image](https://github.com/user-attachments/assets/d2c08d6c-73c9-4d12-8c86-45d68af0b35e)


#### PLOTTING THE DATA:

![image](https://github.com/user-attachments/assets/d70592f9-8699-483d-baca-7c0922df0371)


#### SEASONAL PLOT REPRESENTATION :

![image](https://github.com/user-attachments/assets/a9bd529f-f9d5-4f84-80ae-46a6de21f5f5)


#### TREND PLOT REPRESENTATION :


![image](https://github.com/user-attachments/assets/1a82504d-b4d5-4600-8ef0-e2958e858b9b)


#### RESIDUAL PLOT REPRESENTATION:
![image](https://github.com/user-attachments/assets/5ad9d4c9-118d-4479-9f95-c2f1843dcfd4)




### RESULT:
Thus we have created the python code for the time series analysis and decomposition.
