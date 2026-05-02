# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)
## Date: 02.05.2026
## NAME: MOHAMED NIZAMUDDIN A
## REG NO: 212224040194

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
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd
import os

# Path to the dataset provided
file_path = "/content/DailyDelhiClimateTrain.csv"

# Load the dataset
df = pd.read_csv(file_path)

# Select the 'humidity' column for analysis
data = df['humidity'].values
N = len(data)
lags = range(35)
autocorr_values = []

# Calculate mean and variance
mean_data = np.mean(data)
variance_data = np.var(data)

# Compute Autocorrelation Function (ACF) manually
for lag in lags:
    if lag == 0:
        autocorr_values.append(1.0)
    else:
        # Covariance at specific lag
        auto_cov = np.sum((data[:-lag] - mean_data) * (data[lag:] - mean_data)) / N
        autocorr_values.append(auto_cov / variance_data)

# Generate the visualization
plt.figure(figsize=(12, 6))
plt.stem(lags, autocorr_values)
plt.title('Autocorrelation of Humidity (Daily Delhi Climate)')
plt.xlabel('Lag (Days)')
plt.ylabel('Autocorrelation')
plt.axhline(y=0, color='black', linestyle='-')
plt.grid(True, linestyle='--', alpha=0.7)
plt.show()

# Display summary statistics
display(df[['humidity']].describe())
```
### OUTPUT:
<img width="1001" height="547" alt="image" src="https://github.com/user-attachments/assets/9fe363b1-934b-448b-b875-fb698bb9b662" />

### RESULT:
Thus we have successfully implemented the auto correlation function in python.
