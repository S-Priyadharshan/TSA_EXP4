# Ex.No:04   FIT ARMA MODEL FOR TIME SERIES
# Date: 16/09/2025

### AIM:
To implement ARMA model in python.
### ALGORITHM:
1. Import necessary libraries.
2. Set up matplotlib settings for figure size.
3. Define an ARMA(1,1) process with coefficients ar1 and ma1, and generate a sample of 1000

data points using the ArmaProcess class. Plot the generated time series and set the title and x-
axis limits.

4. Display the autocorrelation and partial autocorrelation plots for the ARMA(1,1) process using
plot_acf and plot_pacf.
5. Define an ARMA(2,2) process with coefficients ar2 and ma2, and generate a sample of 10000

data points using the ArmaProcess class. Plot the generated time series and set the title and x-
axis limits.

6. Display the autocorrelation and partial autocorrelation plots for the ARMA(2,2) process using
plot_acf and plot_pacf.
### PROGRAM:

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.arima_process import ArmaProcess
from statsmodels.graphics.tsaplots import plot_acf, plot_pacf

data = pd.read_csv("/content/co2_gr_mlo.csv", comment="#")

data['Total'] = data['ann inc'] + data['unc']

yearly_total = data.groupby('year')['Total'].sum()

plt.rcParams['figure.figsize'] = [10, 7.5]

ar1 = np.array([1, 0.33])
ma1 = np.array([1, 0.9])
ARMA_1 = ArmaProcess(ar1, ma1).generate_sample(nsample=len(yearly_total))

plt.plot(ARMA_1)
plt.title('Simulated ARMA(1,1) Process for ann_inc + unc')
plt.xlim([0, 200])
plt.show()

plot_acf(ARMA_1)
plot_pacf(ARMA_1)
plt.show()

ar2 = np.array([1, 0.33, 0.5])
ma2 = np.array([1, 0.9, 0.3])
ARMA_2 = ArmaProcess(ar2, ma2).generate_sample(nsample=len(yearly_total) * 10)

plt.plot(ARMA_2)
plt.title('Simulated ARMA(2,2) Process for ann_inc + unc')
plt.xlim([0, 200])
plt.show()

plot_acf(ARMA_2)
plot_pacf(ARMA_2)
plt.show()
```

### OUTPUT:
SIMULATED ARMA(1,1) PROCESS:

<img width="838" height="643" alt="image" src="https://github.com/user-attachments/assets/78027f2f-2e43-43e8-813c-0213260c8a9c" />

Partial Autocorrelation

<img width="847" height="643" alt="image" src="https://github.com/user-attachments/assets/33194709-04b2-484c-a732-3f7719e6afdd" />

Autocorrelation

<img width="847" height="643" alt="image" src="https://github.com/user-attachments/assets/9adfdb74-b5cc-4755-84ae-ed4dc99742cd" />

SIMULATED ARMA(2,2) PROCESS:

<img width="838" height="643" alt="image" src="https://github.com/user-attachments/assets/08efe0b2-04b2-4215-9226-447e04b74093" />

Partial Autocorrelation

<img width="847" height="643" alt="image" src="https://github.com/user-attachments/assets/08ab9f92-2131-4d64-b044-4e43a82ffb16" />

Autocorrelation

<img width="847" height="643" alt="image" src="https://github.com/user-attachments/assets/6ac5d86f-2020-4801-9290-3779d01bb452" />

RESULT:
Thus, a python program is created to fir ARMA Model successfully.
