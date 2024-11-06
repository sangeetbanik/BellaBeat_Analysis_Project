# Combination and cleaning using Python
- Combined the required tables from **12 May 2016 to 11 April 2016** and **12 April 2016 to 12 May 2016**.
```PYTHON
#import all necessary libraries
import pandas as pd 
import numpy as np 
import matplotlib.pyplot as plt 
import seaborn as sns 
import scipy as stats 
from scipy.stats import pearsonre
from sklearn.linear_model import LinearRegression 
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

- checked for missing values, duplicates, outliers, inconsistencies, and errors within the tables before combining them.

```PYTHON
#checking or nulls and duplicates in Daily_activity dataframe
missing_df = df_activity.isnull().sum()
print(missing_df) #prints the number of missing values in each column

duplicate_df = df_activity.duplicated().sum()
print("no.of duplicates:", duplicate_df) #prints the number of duplicate rows in the dataframe

#checking or nulls and duplicates in sleep_daily dataframe
missing_sleep  = sleep.isnull().sum()
print(f"Missing sleep: {missing_sleep}")

duplicate_sleep = sleep.duplicated().sum()
print("no.of duplicates:", duplicate_sleep) #prints the number of duplicate rows in the dataframe

#checking or nulls and duplicates in hourly_activity dataframe
missing_hourly  = df_hourly.isnull().sum()
print(f"Missing values: {missing_hourly}")

duplicate_hr = df_hourly.duplicated().sum()
print("no.of duplicates:", duplicate_hr) #prints the number of duplicate rows in the dataframe
```
- checked for the datatypes of all the variables in the tables.
```PYTHON
#checking the datatypes and changing them if necessary
df_activity.info()
```
![Screenshot 2024-11-06 160023](https://github.com/user-attachments/assets/23df4b15-eaef-4968-b496-91bd7e1fd0db)
```PYTHON
df_activity['ActivityDate'] = pd.to_datetime(df_activity['ActivityDate'], format= '%m/%d/%Y') #to change ActivityDate from object type to datetime type
```
```PYTHON
#checking the datatypes and changing them if necessary
sleep.info()
```
![Screenshot 2024-11-06 161120](https://github.com/user-attachments/assets/9846a6b0-ec0e-4dc2-84df-b1566cdf8583)
```PYTHON
sleep['Sleep_Day'] = sleep['Sleep_Day'].astype('datetime64[ns]')
```
```PYTHON
#checking the datatypes and changing them if necessary
df_hourly.info()
```
![Screenshot 2024-11-06 161711](https://github.com/user-attachments/assets/cc9d8324-fbe4-44b0-8254-b7b526710b21)
```PYTHON
df_hourly['ActivityDate'] = df_hourly['ActivityDate'].astype('datetime64[ns]')
```  
- analysing the general statistics of each table check or any outliers 
```PYTHON
df_activity.describe(include = 'all')
```
![Screenshot 2024-11-06 162929](https://github.com/user-attachments/assets/01d70b17-03bd-4fb9-a6a7-25aac956b435)

```PYTHON
sleep.describe(include = 'all')
```
![Screenshot 2024-11-06 162811](https://github.com/user-attachments/assets/472e8393-d5d2-4f8b-9dc9-fc423fde890d)

```PYTHON
df_hourly.describe(include = 'all')
```
![Screenshot 2024-11-06 162731](https://github.com/user-attachments/assets/c206f56e-d164-4d6a-9e6f-1cbb569dd4d2)




  
