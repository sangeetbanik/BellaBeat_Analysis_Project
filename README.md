# Bellabeat : Smart Device Analysis Project

## 📝 Introduction 
The analysis will concentrate on consumer data regarding a company's marketing strategy and generate insights that back a company's strategy. Bellabeat is the story of a small-scale business that has excelled by producing advanced health-related products for women specifically. Based on the words of one of its co-founders, chief creative officer, and Urška Sršen, data from smart devices might uncover hidden trends within consumers. As we analyzed the users' data, we began detecting patterns in their sleep habit, inactivity, or level of activity. This analysis will outline such trends and provide strategic recommendations for marketing Bellabeat's products.

## 💬 Background
Working for a high-tech company that makes health-focused products for women, I am a junior data analyst working on Bellabeat's marketing analysis team. This is a successful small company, which could be the next major player in the global smart device market. Urška Sršen, co-founder and Chief Creative Officer of Bellabeat, believes that analyzing fitness data from smart devices could uncover new growth opportunities. I will focus on one of the Bellabeat products to collect data from smart devices that understand how consumers use the product. The findings will serve as a basis for making recommendations on the direction that the company's marketing should take, which I will then present to the Bellabeat executive team.

## ⚙ Approach/Steps
### 1. Ask
**Business Task -** analyze smart device usage data to gain insights into how consumers interact with non-Bellabeat smart devices, then choose one Bellabeat product to apply these insights to in your presentation.

> Questions for guiding future marketing program: 
> 1. What are some trends in smart device usage?
> 2. How could these trends apply to Bellabeat customers?
> 3. How could these trends help influence Bellabeat marketing strategy?

### 2. Prepare
#### 🔗 Quick Links
**Data Source:** [FitBit Fitness Tracker Data](https://www.kaggle.com/arashnic/fitbit) <br>
[CC0: Public Domain, dataset made available through [Mobius](https://www.kaggle.com/arashnic)]

This Kaggle dataset presents personal data from thirty users of Fitbit. Thirty such eligible Fitbit users had agreed to let their personal tracker data be submitted and contains minute-level outputs about physical activity, heart rate, and sleep monitoring. The data set entails information about daily activity, steps, and heart rate, which can be useful in analyzing the habits of the users.

#### Considerations
* There may be sampling bias since it is unclear how participants are selected. Participants who are willing to share their activity data publicly may also be more frequent users of Fitbit.
* The dataset does not provide information about gender of the users. Bellabeat is a tech-driven wellness company for women only.
* The data is from 2016, so it is outdated as fitness trackers matured a lot since then.

**Tools:** <br>
- Data pre-processing - Excel.
- Data cleaning & combining - Python.
- Exploratory Data analysis - SQl and Python
- Data visualization - [Tableau](https://public.tableau.com/app/profile/sangeet.banik/viz/BellabeatProject_17307219480650/Coverpage)

### 3. Process
The basis for this analysis is **12-03-2016 to 12-05-2016** data and the steps for processing the data are as follow:
1) [Data Pre-processing]()
2) [Data combination]()
3) [Data cleaning]()
4) [Exploratory_Data Analysis]()

* The "Id" column indicates the number of unique users represented in the dataset. There were 24 unique users who provided data for their 'daily_sleep' health metrics, 8 unique users for their 'weight_loginfo' health metrics, and 35 unique users for the remaining data. Given the very low sample size of 'weight_loginfo' data providers, I have decided to exclude this data frame along with the 'daily_sleep' data from my analysis, as they do not contribute significant insights. Instead, I have utilized the **'daily_activity,' 'hourly_calories,' 'hourly_intensities,' 'hourly_steps,' data tables for my analysis, all of which include inputs from 35 unique users, and 'sleep_day' table, which contain 24 unique users**.

#### Data Exploration & Cleaning
My initial step was to check the individual tables one by one using **Excel** to determine the **data type** and to  uncover any **missing values, outliers, inconsistencies, and errors** within the tables. 
Later, I have used both **SQL** and **Python** to check null values, outliers, inconsistencies, and errors within the tables.
I have perormed the General Statistical Analysis for all the three final tables on **Python**.

The **daily_activity** data set consists of **15 variables**, as shown in the following: <br>
| **No.**|  **Variable**              |  **Description**                                        |
|--------|----------------------------| --------------------------------------------------------|
| 1      | Id                         | Unique ID assigned to each user                         |
| 2      | ActivityDate               | Date of the Log                                         |
| 3      | TotalSteps                 | Total steps taken in a day                              |
| 4      | TotalDistance              | Total distance in a day                                 |
| 5      | TrackerDistance            | Total distance recorded in tracker                      |
| 6      | LoggedActivitiesDistance   |                                                         |
| 7      | VeryActiveDistance         | Distance covered while doing very active movements      |
| 8      | ModeratelyActiveDistance   | Distance covered while doing moderate movements         |
| 9      | LightActiveDistance        | Distance covered while doing light movements            |
| 10     | SedentaryActiveDistance    | Distance covered while doing sedentary movements        |
| 11     | VeryActiveMinutes          | Total time in a day involved in very active movements   |
| 12     | FairlyActiveMinutes        | Total time in a day involved in fairly active movements |                            
| 13     | LightlyActiveMinutes       | Total time in a day involved in lighth movements        | 
| 14     | SedentaryMinutes           | Total time in a day involved in vsedentary movements    |
| 15     | Calories                   | Calories burned in a day                                |

and the **data type** of each variable is depicted below:

<img width="352" alt="DataType" src="">

The **hourly_calories** data set consists of **3 variables**, as shown in the following: <br>
| **No.**|  **Variable**              |  **Description**                                        |
|--------|----------------------------| --------------------------------------------------------|
| 1      | Id                         | Unique ID assigned to each user                         |
| 2      | ActivityDate               | Date of the Log                                         |
| 3      | Calories                   | Calories burned in an hour                              |

and the **data type** of each variable is depicted below:

<img width="352" alt="DataType" src="">


The **hourly_steps** data set consists of **3 variables**, as shown in the following: <br>
| **No.**|  **Variable**              |  **Description**                                        |
|--------|----------------------------| --------------------------------------------------------|
| 1      | Id                         | Unique ID assigned to each user                         |
| 2      | ActivityDate               | Date of the Log                                         |
| 3      | StepTotal                  | Total steps taken in an hour                            |

and the **data type** of each variable is depicted below:

<img width="352" alt="DataType" src="">

The **hourly_intensities** data set consists of **4 variables**, as shown in the following: <br>
| **No.**|  **Variable**              |  **Description**                                        |
|--------|----------------------------| --------------------------------------------------------|
| 1      | Id                         | Unique ID assigned to each user                         |
| 2      | ActivityDate               | Date of the Log                                         |
| 3      | TotalIntensity             | intensity in an hour                                    |
| 4      | AverageIntensity           | Total distance recorded in tracker                      |

and the **data type** of each variable is depicted below:

<img width="352" alt="DataType" src="">



The **sleep_day** data set consists of **6 variables**, as shown in the following: <br>
| **No.**|  **Variable**              |  **Description**                                        |
|--------|----------------------------| --------------------------------------------------------|
| 1      | Id                         | Unique ID assigned to each user                         |
| 2      | SleepDay                   | Date of the Log                                         |
| 3      | Sleep_time                 | Time of the Log                                         |
| 4      | TotalSleepRecords          | Totalno.of logs                                         |
| 5      | TotalMinutesAsleepy        | Total mins of sleep                                     |
| 6      | TotalTimeInBed             | Total mins lying on bed                                 |

and the **data type** of each variable is depicted below:

<img width="352" alt="DataType" src="">

#### Data Pre-processing & Combining
As mentioned earlier,the 5 tables from **12 May 2016 to 11 April 2016** and 5 tables from **12 April 2016 to 12 May 2016** were stacked and combined.

* Pre-processing : combination of 'hourly_calories,' 'hourly_intensities,' 'hourly_steps,' tables,from **12 May 2016 to 11 April 2016** and from **12 April 2016 to 12 May 2016** , into two tables i.e. **hourly_activity_1** and **hourly_activity_2**, respectively, was done using **Excel**.
  
The **hourly_activity**[i.e. combination of **hourly_activity_1** and **hourly_activity_2** ] data set consists of **7 variables**, as shown in the following: <br>
| **No.**|  **Variable**              |  **Description**                                        |
|--------|----------------------------| --------------------------------------------------------|
| 1      | Id                         | Unique ID assigned to each user                         |
| 2      | ActivityDate               | Date of the Log                                         |
| 3      | ActivityHour               | Hour of the Log                                         |
| 4      | StepTotal                  | Total steps taken in an hour                            |
| 5      | TotalIntensity             | intensity in an hour                                    |
| 6      | AverageIntensity           | Total distance recorded in tracker                      |
| 7      | Calories                   | Calories burned in an hour                              |

and the **data type** of each variable is depicted below:

<img width="352" alt="DataType" src="">
  - Combining of tables was done using **Python**. The final table consists of 46183 rows.
 
* Added 3 new columns to **daily_activity** table : **'Day_of_week	,' 'Total_active_mins,' and 'Total_active_hours'**.
     
The **daily_activity** data set consists of **18 variables**, as shown in the following: <br>
| **No.**|  **Variable**              |  **Description**                                        |
|--------|----------------------------| --------------------------------------------------------|
| 1      | Id                         | Unique ID assigned to each user                         |
| 2      | ActivityDate               | Date of the Log                                         |
| 3      | Day_of_week                | Day of the Log                                          |
| 4      | TotalSteps                 | Total steps taken in a day                              |
| 5      | TotalDistance              | Total distance in a day                                 |
| 6      | TrackerDistance            | Total distance recorded in tracker                      |
| 7      | LoggedActivitiesDistance   |                                                         |
| 8      | VeryActiveDistance         | Distance covered while doing very active movements      |
| 9      | ModeratelyActiveDistance   | Distance covered while doing moderate movements         |
| 10     | LightActiveDistance        | Distance covered while doing light movements            |
| 11     | SedentaryActiveDistance    | Distance covered while doing sedentary movements        |
| 12     | VeryActiveMinutes          | Total time in a day involved in very active movements   |
| 13     | FairlyActiveMinutes        | Total time in a day involved in fairly active movements |                            
| 14     | LightlyActiveMinutes       | Total time in a day involved in lighth movements        | 
| 15     | SedentaryMinutes           | Total time in a day involved in vsedentary movements    |
| 16     | Total_active_mins          | Total time of activity in  mins                         |
| 17     | Total_active_hours         | Total time of activity in  hours                        |
| 18     | Calories                   | Calories burned in a day                                |

and the **data type** of each variable is depicted below:

<img width="352" alt="DataType" src="">

*Added 2 new columns to **sleep_day** table : **'Day_of_week' and 'AwakeInBedTime'**.
     
The **sleep_day** data set consists of **8 variables**, as shown in the following: <br>
| **No.**|  **Variable**              |  **Description**                                        |
|--------|----------------------------| --------------------------------------------------------|
| 1      | Id                         | Unique ID assigned to each user                         |
| 2      | SleepDay                   | Date of the Log                                         |
| 3      | Sleep_time                 | Time of the Log                                         |
| 4      | Day_of_week                | Name of the day                                         |
| 5      | TotalSleepRecords          | Totalno.of logs                                         |
| 6      | TotalMinutesAsleepy        | Total mins of sleep                                     |
| 7      | TotalTimeInBed             | Total mins lying on bed                                 |
| 8      | AwakeInBedTime             | Total mins awake in bed                                 |

and the **data type** of each variable is depicted below:

<img width="352" alt="DataType" src="">

* Combination of **daily_activity** table and **sleep_day** table was done using **Python**. The final tables consists of 1397 rows and 413 rows respectively.
* I'll be using these three tables for future analysis.

### 4. Analyze
#### Data Analysis
The analysis question is: 
> What are some trends in smart device usage?

Transform the data to identify patterns and draw conclusions.The cleaned data is imported into Tableau for analysis and the figures plotted are displayed in the following.

### - Time Spent in A Day
The figure below shows the distribution of how **Time spent in a day** by the 35 distinct user. 

![Activity Level]()

- **82% of User's time** is recorded as **sedentary activity**.
- While only **1% stays fairly active** and **2% stays very active**. 
<br>

### - Average Steps per User
The figure below shows the **Average steps taken per day** by the 35 distinct user. 

![Average steps per User]()

- **20% of Users** are able to hit atleast 10k steps daily.
- While **80% of Users** all below the recommended range. 
<br>

### - Activity duration and Calories burned in day
The figure below shows the relation between **Type of activity and calories burned** by the 35 distinct user in a day. 

![Activity Vs Calories]()

- There is a strong **positive correlation**. 
#### Key Findings:

* The R-Squared value for Low Active graph is 0.19
* The R-Squared value for Fairly Active graph is 0.084
* The R-Squared value for Very Active graph is 0.326

There is a strong correlation between Very Active minutes and the amount of calories burned. The r-squared value seems to rise as the intensity and the duration is the activity increases. Thus by inferring to the r-squared values of the respective trend lines of the graphs, we can conclude that the higher the intensity and the duration of the activity, the more calories is burned.
<br>

### - Total distance,Tracker distance, Total steps and Calories burned in day
The figure below shows the relation between **Total distance,Tracker distance, Total steps and calories burned** by the 35 distinct user in a day. 

![Total distance,Tracker distance, Total steps and Calories burned in day]()

- There is a strong **positive correlation**. 
#### Key Findings:

* The R-Squared value for Total distance graph is 0.3919
* The R-Squared value for Tracker distance graph is 0.3915
* The R-Squared value for Total Steps graph is 0.3346

There is a strong correlation between activity and the amount of calories burned. The r-squared value seems to rise as the intensity of the activity increases. Thus by inferring to the r-squared values of the respective trend lines of the graphs, we can conclude that the higher the intensity of the activity, the more calories is burned.
<br>

### - Distance covered per type of activity in a day
The figure below shows the distribution of **distance covered per type of activity** by the 35 distinct user in a day. 

![Distance per activity Distribution]()

- **Lightly active movements** cover the majority of the distance i.e. **61% o total distance covered in a day* .
- **27%** accounts to **very active movements** and **10%** to **fairly active movements**.

### - Most Active hour of the day
The figure below shows the **Most desired time for workout**.
![]()

- **No correlation** between the activity level and sleep duration.
- Thus we can say they are not correlated in any way.

### - Activity duration and sleep duration
The figure below shows the relation between **duration of various activity and sleep duartion**.
![Activity Level vs Sleep]()

- **No correlation** between the activity level and sleep duration.
- Thus we can say they are not correlated in any way.

### - Total sleep miniutes and Calories burned in day
The figure below shows the relation between **Total sleeping time and calories burned** . 

![Sleep Time Vs Calories burned]()

- There is a strong **positive correlation**. 
#### Key Findings:

* The R-Squared value for Total distance graph is 0.871
  
Higher duration of sleep is associated with higher amount of calories burned. An adequate duration and good quality of sleep constitutes to higher calories burned during the sleeping process. However sleeping more than the required range doesn't seem to burn more calories and in fact causes the opposite to occur, which is burn fewer calories.
<br>

### 5. Share
![BellaBeat: Smart Device Analysis Dashboard]()

View [BellaBeat: Smart Device Analysis Dashboard]().

### 6. Act
#### <ins>Recommendations</ins>
To develop new marketing strategies aimed at unlocking growth opportunities and expanding the business, we should refer to the analysis above and consider those insights. Below are my key recommendations for addressing this business scenario.

Primary Recommendations for Marketing Strategists:

* The general practice of consumers is most likely idle; thus, they turn into a sedentary person. Smart device notices given between the peak working hours of 7:00 AM to 8:00 PM can activate someone by reminding them to start the device and encourage an active lifestyle.
*  Push notifications through the application to remind users to get adequate sleep each night, and introduce REM sleep monitoring as an indication of quality sleep.
*   Conduct a daily or weekly calorie competition in which the best scorers earn points. These points can be accumulated and used for future reductions when purchasing goods.

## 🔮 Conclusion
After collecting, transforming, cleaning, organizing, and analyzing the datasets as requested, we now have enough evidence to answer the questions presented regarding the businesses.

Thus, we can conclude that duration and intensity of the activity are directly proportional to calories burnt. 

Most consumers seem to get enough sleep but with a small portion getting excessive sleep or too low an amount of sleep.

The consumers are likely to take part in low up to high-intensity activity during 7:00 AM to 8:00 PM.





























