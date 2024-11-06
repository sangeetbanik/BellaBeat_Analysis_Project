# Combination and cleaning using Python
- Combined the required tables from **12 May 2016 to 11 April 2016 and 12 April 2016 to 12 May 2016**.
```PYTHON
#import all necessary libraries
import pandas as pd # type: ignore
import numpy as np # type: ignore
import matplotlib.pyplot as plt # type: ignore
import seaborn as sns # type: ignore
import scipy as stats # type: ignore
from scipy.stats import pearsonr # type: ignore
from sklearn.linear_model import LinearRegression # type: ignore
print("import successful")

#read 'daily_activity' csv files
daily_ac_1 = pd.read_csv(r"Fitabase Data 3.12.16-4.11.16\required files\dailyActivity_merged.csv")
daily_ac_2  =pd.read_csv(r"Fitabase Data 4.12.16-5.12.16\required files\dailyActivity_merged.csv")
print("read successful")

#combining the two tables of daily_activity
files = [r"Fitabase Data 3.12.16-4.11.16\required files\dailyActivity_merged.csv",r"Fitabase Data 4.12.16-5.12.16\required files\dailyActivity_merged.csv"]
df_activity = pd.concat(pd.read_csv(file) for file in files)
df_activity.reset_index(drop = True, inplace = True)
print("combining successful")

#read 'hourly_activity'csv files
hourly_ac_1 = pd.read_csv(r"Fitabase Data 3.12.16-4.11.16\required files\hourly_activity.csv")
hourly_ac_2  =pd.read_csv(r"Fitabase Data 4.12.16-5.12.16\required files\hourly_activity.csv")
print("read successful")

#combining the two tables of hourly_activity
files = [r"Fitabase Data 3.12.16-4.11.16\required files\hourly_activity.csv",r"Fitabase Data 4.12.16-5.12.16\required files\hourly_activity.csv"]
df_hourly = pd.concat(pd.read_csv(file) for file in files)
df_hourly.reset_index(drop = True, inplace = True)
print("combining successful")

```






- checked for missing values, outliers, inconsistencies, and errors within the tables before combining them.



  
