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


#### Data Pre-processing & Combining
As mentioned earlier,the 5 tables from **12 May 2016 to 11 April 2016** and 5 tables from **12 April 2016 to 12 May 2016** were stacked and combined.

* pre-processing of **hourly_activity**[i.e. combination of 'hourly_calories,' 'hourly_intensities,' 'hourly_steps,' tables] table was done using **excel** and then concatenation using **Python**. The final consists of 46183 rows.
* combination of **daily_activity** table and **sleep_day** table was done using **Python**. The final tables consists of 1397 rows and 413 rows respectively.


















