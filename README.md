# TSA-Ex-3
# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)


### AIM:
To Compute the AutoCorrelation Function (ACF) of the data for the first 35 lags to determine the model
type to fit the data.

Dataset used:
ice_cream

Software Required:
Google colab


### ALGORITHM:
1. Import the necessary packages
2. Find the mean, variance and then implement normalization for the data.
3. Implement the correlation using necessary logic and obtain the results
4. Store the results in an array
5. Represent the result in graphical representation as given below.
### PROGRAM:

```

import pandas as pd
import matplotlib.pyplot as plt
import numpy as np

# Read dataset
data = pd.read_csv('/content/ice_cream.csv')

data.head()

# Get numerical column
values = data['IPN31152N'].dropna().values

# Calculate length
N = len(values)

# Define lags
lags = range(35)

autocorr_values = []

# Calculate mean and variance
mean_data = np.mean(values)
variance_data = np.var(values)

normalized_data = (values - mean_data) / np.sqrt(variance_data)

# Calculate autocorrelation for each lag
for lag in lags:
    if lag == 0:
        autocorr_values.append(1)
    else:
        auto_cov = np.sum(
            (values[:-lag] - mean_data) *
            (values[lag:] - mean_data)
        ) / N

        autocorr_values.append(auto_cov / variance_data)

# Display the graph
plt.figure(figsize=(10, 6))

plt.stem(lags, autocorr_values)

plt.title('Autocorrelation of Ice Cream Data')
plt.xlabel('Lag')
plt.ylabel('Autocorrelation')

plt.grid(True)
plt.show()
```


### OUTPUT:

<img width="584" height="321" alt="image" src="https://github.com/user-attachments/assets/161e8288-a4e8-4bd9-a30c-ae1ec5d6dbeb" />


### RESULT:
        Thus we have successfully implemented the auto correlation function in python.
