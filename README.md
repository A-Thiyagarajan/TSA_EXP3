#### Development by Thiyagarajan A
#### Register no: 212222240110
#### Date:
# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)

### AIM:
To Compute the AutoCorrelation Function (ACF) of the data for the first 35 lags to determine the model
type to fit the data.
### ALGORITHM:
1. Import the necessary packages
2. Find the mean, variance and then implement normalization for the data.
3. Implement the correlation using necessary logic and obtain the results
4. Store the results in an array
5. Represent the result in graphical representation as given below.
### PROGRAM:
```
import numpy as np
import pandas as pd
import statsmodels.api as sm
import matplotlib.pyplot as plt

# Load the data from the CSV file

df = pd.read_csv('Google_Stock_Price_Train.csv')

# Extract the 'Open' column (you can replace this with another column if needed)
data = df['Open'].values

# Calculate mean and variance
data_mean = np.mean(data)
data_var = np.var(data)

# Normalize the data
normalized_data = (data - data_mean) / np.sqrt(data_var)

# Compute the autocorrelation function (ACF)
acf_result = np.correlate(normalized_data, normalized_data, mode='full')
acf_result = acf_result[len(acf_result)//2:]  # Keep only positive lags

# Plot the ACF result
plt.figure(figsize=(10, 5))
plt.stem(acf_result[:36], use_line_collection=True)  # Plot only the first 36 lags
plt.xlabel('Lag')
plt.ylabel('Autocorrelation')
plt.title('Autocorrelation Function (ACF) of Google Stock Prices')
plt.show()

```

### OUTPUT:
![WhatsApp Image 2024-09-23 at 11 45 31_a968d356](https://github.com/user-attachments/assets/35d9344e-e8e6-40fc-8a61-57b7793b5854)


### RESULT:
Implementation of auto correlation function in python was successfully completed .
