# Exploratory Data Analysis using Python
```PYTHON
plt.hist(df_activity.Day_of_week, bins = 7, 
         width = 0.6, color = "blue", edgecolor = "black")

plt.xlabel("Day of the week")
plt.ylabel("Frequency")
plt.title("No. of times users logged in app across the week")

ax= plt.gca()
for p in ax.patches:
    height = p.get_height()
    ax.text(p.get_x()+p.get_width()/2., height + 0.1,
            '{:1.0f}'.format(height), ha="center")   
plt.show()
```
![output](https://github.com/user-attachments/assets/9d395782-69b5-4557-a39e-a478c4a9c5b2)

```PYTHON
x = df_activity['TotalSteps']
y = df_activity['Calories']

mean_steps = x.mean()
mean_calories = y.mean()

plt.scatter(x,y,alpha = 0.8, c = y, 
            cmap = "Spectral")
plt.xlabel("Steps taken")
plt.ylabel("Calories burned")
plt.axvline(mean_steps, color = 'blue', label = 'Mean steps')
plt.axhline(mean_calories, color = 'red' , label = 'Mean calories')
plt.title("Calories burned for every step taken")
plt.colorbar(label = "Calories")
plt.legend()

plt.show()
```
![output2](https://github.com/user-attachments/assets/5e01a4f1-a7d8-4f6a-b383-6d6b54ecf3dd)

```PYTHON
very_active_mins = df_activity['VeryActiveMinutes'].sum()
fairly_active_mins = df_activity['FairlyActiveMinutes'].sum()
lightly_active_mins = df_activity['LightlyActiveMinutes'].sum()
sedentary_mins = df_activity['SedentaryMinutes'].sum()

slices = [very_active_mins, fairly_active_mins, lightly_active_mins, sedentary_mins]
labels = ["Very active minutes", "Fairly active minutes", "Lightly active minutes", "Sedentary minutes"]
colours = ["orange", "yellowgreen", "skyblue", "pink"]
explode = [0, 0, 0, 0.1]
plt.pie(slices, labels = labels, 
        colors = colours, wedgeprops = {"edgecolor": "black"}, 
        explode = explode, autopct = "%1.1f%%")
plt.title("Percentage of Activity in Minutes")

plt.show()
```
![output3](https://github.com/user-attachments/assets/0d841bbb-6bde-4af5-88ea-21dfe573148b)

```PYTHON
x_2 = df_activity['TotalDistance']
y_2 = df_activity['Calories']

mean_active_distance = df_activity['VeryActiveDistance'].mean()
mean_light_distance  = df_activity['LightActiveDistance'].mean()
mean_mod_distance = df_activity['ModeratelyActiveDistance'].mean()
mean_sedentary_distance = df_activity['SedentaryActiveDistance'].mean()
mean_calories = df_activity['Calories'].mean()
plt.scatter(x_2,y_2, c=y_2, cmap="Spectral")
plt.colorbar(label='Calories')
plt.axvline(mean_active_distance, color = 'red', label = "Mean active Distance")
plt.axvline(mean_light_distance, color = 'green', label = "Mean ligth Distance")
plt.axvline(mean_mod_distance, color = 'orange', label = "Mean moderate Distance")
plt.axvline(mean_sedentary_distance, color = 'purple', label = "Mean sedentary distance")

plt.axhline(mean_calories, color = 'blue', label = "Mean calories")
plt.title('Total Distance vs Calories')
plt.xlabel('distance')
plt.ylabel('calories')
plt.legend()
plt.show()
```
![output4](https://github.com/user-attachments/assets/dc3428e1-5f52-47bf-9bfa-8c8251b30265)

```PYTHON
result = df_activity.groupby('Day_of_week').agg(
    total_steps=('TotalSteps', 'sum'),
    total_distance=('TotalDistance', 'sum'),
    total_calories=('Calories', 'sum')
).reset_index()

fig, ax = plt.subplots(1,3, figsize=(25, 10))

sns.barplot(x='Day_of_week',y='total_steps', data=result, color='purple', ax=ax[0])
ax[0].set_title('Distribution of total steps in a week', fontsize=15)
ax[0].set_xlabel('Days', fontsize=12)
ax[0].set_ylabel('Total Steps', fontsize=12)
for p in ax[0].patches:
    height = p.get_height()
    ax[0].text(p.get_x()+p.get_width()/2., height + 0.1,
            '{:1.0f}'.format(height), ha="center") 



sns.barplot(x='Day_of_week',y='total_distance', data=result,color='green', ax=ax[1])
ax[1].set_title('Distribution of total distance in a week', fontsize=15)
ax[1].set_xlabel('Days', fontsize=12)
ax[1].set_ylabel('Total distance', fontsize=12)
for p in ax[1].patches:
    height = p.get_height()
    ax[1].text(p.get_x()+p.get_width()/2., height + 0.1,
            '{:1.0f}'.format(height), ha="center") 
    

sns.barplot(x='Day_of_week',y='total_calories', data=result,color='orange', ax=ax[2])
ax[2].set_title('Distribution of total calories in a week', fontsize=15)
ax[2].set_xlabel('Days', fontsize=12)
ax[2].set_ylabel('Total calories', fontsize=12)
for p in ax[2].patches:
    height = p.get_height()
    ax[2].text(p.get_x()+p.get_width()/2., height + 0.1,
            '{:1.0f}'.format(height), ha="center") 


plt.show()
```
![output5](https://github.com/user-attachments/assets/177adcd4-2c96-4148-8efe-8316f0ca1f53)

```PYTHON
result_total_mins = df_activity.groupby('Id').agg(
    Total_steps = ('TotalSteps','sum'),
    Total_veryactive = ('VeryActiveMinutes','sum'),
    Total_fairlyactive = ('FairlyActiveMinutes','sum'),
    Total_lightlyactive = ('LightlyActiveMinutes','sum'),
    Total_sedentary = ('SedentaryMinutes','sum'),
    Total_calories = ('Calories','sum')
    ).reset_index()
print(result_total_mins)
r_value1, _ = pearsonr(result_total_mins['Total_veryactive'],result_total_mins['Total_calories'])
r_value2, _ = pearsonr(result_total_mins['Total_calories'], result_total_mins['Total_fairlyactive'])
r_value3, _ = pearsonr(result_total_mins['Total_calories'], result_total_mins['Total_lightlyactive'])
r_value4, _ = pearsonr(result_total_mins['Total_calories'], result_total_mins['Total_sedentary'])


lm = LinearRegression()

fig, ax = plt.subplots(1, 4, figsize=(32, 10))

lm.fit(result_total_mins[['Total_veryactive']],result_total_mins['Total_calories'])
r_sq1 = lm.score(result_total_mins[['Total_veryactive']],result_total_mins['Total_calories'])
sns.regplot(
    x='Total_veryactive',
    y='Total_calories',
    data=result_total_mins,
    color='purple',
    ax=ax[0],
    scatter_kws={'s': 50}  
)
ax[0].set_title('Very Active Minutes vs. Calories Burned', fontsize=15)
ax[0].set_xlabel('Very Active Minutes', fontsize=12)
ax[0].set_ylabel('Total Calories Burned', fontsize=12)
ax[0].text(0.05, 0.95, f'r = {r_value1:.2f}\nR² = {r_sq1:.2f}', transform=ax[0].transAxes, fontsize=12, verticalalignment='top')

lm.fit(result_total_mins[['Total_fairlyactive']],result_total_mins['Total_calories'])
r_sq2 = lm.score(result_total_mins[['Total_fairlyactive']],result_total_mins['Total_calories'])
sns.regplot(
    x='Total_fairlyactive',
    y='Total_calories',
    data=result_total_mins,
    color='green',
    ax=ax[1],
    scatter_kws={'s': 50}  
)
ax[1].set_title('Fairly Active Minutes vs. Calories Burned', fontsize=15)
ax[1].set_xlabel('Fairly Active Minutes', fontsize=12)
ax[1].set_ylabel('Total Calories Burned', fontsize=12)
ax[1].text(0.05, 0.95, f'r = {r_value2:.2f}\nR² = {r_sq2:.2f}', transform=ax[1].transAxes, fontsize=12, verticalalignment='top')

lm.fit(result_total_mins[['Total_lightlyactive']],result_total_mins['Total_calories'])
r_sq3 = lm.score(result_total_mins[['Total_lightlyactive']],result_total_mins['Total_calories'])
sns.regplot(
    x='Total_lightlyactive',
    y='Total_calories',
    data=result_total_mins,
    color='orange',
    ax=ax[2],
    scatter_kws={'s': 50}  
)
ax[2].set_title('Lightly Active Minutes vs. Calories Burned', fontsize=15)
ax[2].set_xlabel('Lightly Active Minutes', fontsize=12)
ax[2].set_ylabel('Total Calories Burned', fontsize=12)
ax[2].text(0.05, 0.95, f'r = {r_value3:.2f}\nR² = {r_sq3:.2f}', transform=ax[2].transAxes, fontsize=12, verticalalignment='top')

lm.fit(result_total_mins[['Total_sedentary']],result_total_mins['Total_calories'] )
r_sq4 = lm.score(result_total_mins[['Total_sedentary']],result_total_mins['Total_calories'])
sns.regplot(
    x='Total_sedentary',
    y='Total_calories',
    data = result_total_mins,
    color='yellow',
    ax=ax[3] ,
    scatter_kws={'s': 50}
)
ax[3].set_title('Sedentary Minutes vs. Calories Burned', fontsize=15)
ax[3].set_xlabel('Sedentary Minutes', fontsize=12)
ax[3].set_ylabel('Total Calories Burned', fontsize=12)
ax[3].text(0.05, 0.95, f'r = {r_value4:.2f}\nR² = {r_sq4:.2f}', transform=ax[3].transAxes, fontsize=12, verticalalignment='top')



plt.show()
```
![output6](https://github.com/user-attachments/assets/41e94c7b-b519-4821-be86-42d14aee1bde)

```PYTHON
daily_sleep_merged = pd.merge(
    daily_activity,
    sleep,
    left_on=['Id', 'ActivityDate'],
    right_on=['Id', 'Sleep_Day'],
    how='inner'
)

# Group by 'Id' and calculate the sum of required columns
result = daily_sleep_merged.groupby('Id').agg(
    total_sleep_min=('TotalMinutesAsleep', 'sum'),
    total_timeinbed_min=('TotalTimeInBed', 'sum'),
    calories=('Calories', 'sum')
).reset_index()

# Display the result
print(result)
r_value_1, _ = pearsonr(result['total_sleep_min'],result['calories'])
r_value_2, _ = pearsonr(result['total_sleep_min'],result['calories'])

lm = LinearRegression()
lm.fit(result[['total_sleep_min']], result['calories'])
r_sq_1 = lm.score(result[['total_sleep_min']], result['calories'])

sns.regplot(
    x="total_sleep_min",
    y="calories",
    data=result,
    color='orange',
    scatter_kws={'alpha': 0.5, 's': 50}
)
plt.title("Sleep Vs Calories burned")
plt.xlabel("Total Sleep(in mins)")
plt.ylabel("Calories Burned")
plt.text(0.05, 0.95, f'r = {r_value_1:.2f}\nR² = {r_sq_1:.2f}', transform=plt.gca().transAxes, fontsize=12, verticalalignment='top')

plt.show()
```
![output7](https://github.com/user-attachments/assets/7548d0e0-e8eb-4ffb-8934-403480e64fb8)



