# Ex.No: 1B                     CONVERSION OF NON STATIONARY TO STATIONARY DATA
# Date: 31.08.2025

### AIM:
To perform regular differncing,seasonal adjustment and log transformatio on international airline passenger data
### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the data preprocessing if needed and apply regular differncing,seasonal adjustment,log transformation.
4. Plot the data according to need, before and after regular differncing,seasonal adjustment,log transformation.
5. Display the overall results.
### PROGRAM:
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

# Load dataset
df = pd.read_csv("AirPassengers.csv", parse_dates=['Month'], index_col='Month')

# Regular differencing (remove trend)
df['Regular Difference'] = df['#Passengers'].diff()

# Seasonal decomposition (period = 12 months)
result = seasonal_decompose(df['#Passengers'], model='additive', period=12)
df['Seasonal Adjustment'] = result.resid

# Log transformation (stabilize variance)
df['Log Transformation'] = np.log(df['#Passengers'])

# Plot transformations
plt.figure(figsize=(14, 10))

plt.subplot(4, 1, 1)
plt.plot(df['#Passengers'], label='Original')
plt.legend(loc='best')
plt.title('Original Data')

plt.subplot(4, 1, 2)
plt.plot(df['Regular Difference'], label='Regular Difference', color='orange')
plt.legend(loc='best')
plt.title('Regular Differencing')

plt.subplot(4, 1, 3)
plt.plot(df['Seasonal Adjustment'], label='Seasonal Adjustment', color='green')
plt.legend(loc='best')
plt.title('Seasonal Adjustment (from decomposition)')

plt.subplot(4, 1, 4)
plt.plot(df['Log Transformation'], label='Log Transformation', color='red')
plt.legend(loc='best')
plt.title('Log Transformation')

plt.tight_layout()
plt.show()
```


### OUTPUT:
Original Data:
<img width="1461" height="257" alt="image" src="https://github.com/user-attachments/assets/e054ddfe-cfb1-46a3-ac5e-7b173d81e29e" />



REGULAR DIFFERENCING:
<img width="1427" height="266" alt="image" src="https://github.com/user-attachments/assets/7cb60189-8846-418b-b238-b12b7cb532f0" />



SEASONAL ADJUSTMENT:
<img width="1427" height="248" alt="image" src="https://github.com/user-attachments/assets/dab0aa39-2c7b-4413-9db0-c0714c54c7fe" />



LOG TRANSFORMATION:
<img width="1433" height="252" alt="image" src="https://github.com/user-attachments/assets/6ae7f421-786d-474d-ad0f-27186477edd6" />



### RESULT:
Thus we have created the python code for the conversion of non stationary to stationary data on international airline passenger
data.
