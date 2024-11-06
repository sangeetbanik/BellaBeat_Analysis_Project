- Initially, I checked all the tables to get familiarise with the datasets.
- 6 tables were chosen from **12 May 2016 to 11 April 2016** and **12 April 2016 to 12 May 2016** respectively. Those are:- 'weight_loginfo', 'daily_activity,' 'hourly_calories,' 'hourly_intensities,' 'hourly_steps,' and  'sleep_day'.
- **'weight_loginfo'** tables contains input from only 8 unique users. Given the very low sample size of 'weight_loginfo' data providers, I have decided to exclude this data frame  as it does not contribute significant insights.
- I have utilized the 'daily_activity,' 'hourly_calories,' 'hourly_intensities,' 'hourly_steps,' and  'sleep_day' data tables for my analysis.
- I combined 'hourly_calories', 'hourly_intensities', and 'hourly_steps' into a single table named as 'hourly_activity'.

- Added 3 new columns to "daily_activity" table : 'Day_of_week ,' 'Total_active_mins,' and 'Total_active_hours'.
    * Day_of_week        = TEXT("ActivityDate","dddd")
    * Total_active_mins  = "VeryActiveMinutes"+"FairlyActiveMinutes"+"LightlyActiveMinutes"+"SedentaryMinutes"
    * Total_active_hours = ("Total_active_mins")/60

- Added 4 new columns to sleep_day table : 'Day_of_week', 'AwakeInBedTime', 'total_sleep_hr' and 'total_timeinbed_hr'.
    * Day_of_week        = TEXT("SleepDay","dddd")
    * AwakeInBedTime     = (TotalTimeInBed - TotalMinutesAsleep)
    * total_sleep_hr     = (TotalMinutesAsleep)/60
    * total_timeinbed_hr = (TotalTimeInBed)/60 
