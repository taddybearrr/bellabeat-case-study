Bellabeat Data Analysis Report

## Table of Contents
1. [Introduction](#introduction)
2. [Data Sources](#data-sources)
3. [Objectives](#objectives)
4. [Analysis Process](#analysis-process)
5. [Key Findings](#key-findings)
    - [Activity vs. Sleep](#activity-vs-sleep)
    - [Activity vs. Heart Rate](#activity-vs-heart-rate)
    - [Sleep Quality and Heart Rate](#sleep-quality-and-heart-rate)
    - [High-Activity Users](#high-activity-users)
6. [Recommendations](#recommendations)
7. [Conclusion](#conclusion)

---

## Introduction

This case study explores data from **Bellabeat**, a high-tech company focused on women's health and wellness. The goal of this project is to analyze user activity, sleep, and heart rate data from April and May 2016 to uncover actionable insights that can enhance Bellabeat’s product offerings. Bellabeat can tailor features and recommendations to optimize user wellness by understanding how activity correlates with sleep and heart health.
Smart devices like Fitbits, Apple Watches, and Bellabeat devices are increasingly used by individuals to monitor their **daily activity, sleep, and overall wellness**. 
Understanding trends in this data will help Bellabeat align its product features with the needs of its target market, particularly women who are tech-savvy and health-conscious.

---

## Data Sources
The data used for this analysis comes from Fitbit's publically available dataset on [Kaggle](https://www.kaggle.com/datasets/arashnic/fitbit). 
This data contains two separate folders: one for the month of Mar-Apr and the second for Apr-May of 2016.

Data includes:
| Fitabase Data 3.12.16-4.11.16    | Fitabase Data 4.12.16-5.12.16        |
|:---------------------------------|:-------------------------------------|
|dailyActivity_merged.csv          |dailyActivity_merged.csv	      	  |
|heartrate_seconds_merged.csv	   |dailyCalories_merged.csv	       	  |
|hourlyCalories_merged.csv         |dailyIntensities_merged.csv	          |
|hourlyIntensities_merged.csv      |dailySteps_merged.csv		          |
|hourlySteps_merged.csv            |heartrate_seconds_merged.csv	      |
|minuteCaloriesNarrow_merged.csv   |hourlyCalories_merged.csv		      |
|minuteIntensitiesNarrow_merged.csv|hourlyIntensities_merged.csv	      |
|minuteMETsNarrow_merged.csv       |hourlySteps_merged.csv		  	      |
|minuteSleep_merged.csv		       |minuteCaloriesNarrow_merged.csv	      |
|minuteStepsNarrow_merged.csv	   |minuteCaloriesWide_merged.csv	      |
|weightLogInfo_merged.csv	       |minuteIntensitiesNarrow_merged.csv	  |
|			                       |minuteIntensitiesWide_merged.csv  	  |
|			                       |minuteMETsNarrow_merged.csv		  	  |
|				                   |minuteSleep_merged.csv	          	  |
|				                   |minuteStepsNarrow_merged.csv      	  |
|				                   |minuteStepsWide_merged.csv		      |
|				                   |sleepDay_merged.csv			          |
|				                   |weightLogInfo_merged.csv	          |


The table above shows that more metrics were tracked in the 2nd month. 
This month contains more data in both narrow and wide formats for minute-by-minute calories, intensities, sleep, and steps.

I paid closer attention to these specific metrics below:
- **Daily Activity Data**: Step counts, active minutes, distance traveled, and calories burned.
- **Minute-Sleep Data**: Total sleep duration, including minutes asleep, restless, and awake.
- **Seconds-Heart Rate Data**: Daily average heart rate activity by seconds.

Analyzing the trends in this data will help Bellabeat understand customer behavior based on how much they move, how well they sleep, and how they recover through heart rate.


The data was processed and cleaned using **SQL** within Google BigQuery, and visualized using **Google Sheets**.

---

## Objectives

The main objectives of this case study are:
- To identify trends in user behavior related to activity, sleep, and heart rate using the public dataset from Fitbit.
- To apply these findings to create actionable insights that Bellabeat can use to improve product features and enhance user engagement.

---

## Analysis Process

### 1. Data Cleaning
The data was cleaned to handle `NULL` values, incorrect or missing entries, and ensure accurate calculations of metrics such as **TotalSleepHrs**, **AvgDailyHeartRate**, and **AvgDailySteps**.

The key steps in the data cleaning process include:
- Aggregating daily data for each user.
- Removing records with incomplete sleep or heart rate data where necessary.
- Normalizing and scaling the data for more effective visualizations and comparisons.

### 2. SQL Queries
We ran SQL queries to explore key relationships in the data, such as:
- The correlation between steps and sleep duration.
- The effect of high activity on heart rate.
- The connection between sleep quality and recovery (via heart rate).

These queries allowed us to uncover trends in **smart device usage**, particularly around tracking activity and wellness metrics, which are central to Bellabeat's products.
For detailed SQL queries used in this analysis, please refer to the [analysis folder](./analysis).

---

## Key Findings

### Activity vs. Sleep

![Steps vs. Sleep](https://github.com/taddybearrr/bellabeat-case-study/blob/dd2bd3db7fc76132c3ceabac5bd6a1a91f8313e0/visualizations/Average%20Sleep%20and%20Steps%20by%20User.pdf)

- **Observation**: The correlation coefficient is approximately -0.10, indicating a weak negative correlation, but the relationship between steps and heart rate is not particularly strong. Users with high daily steps, such as user `4388161847` (11,198 steps), exhibit varying levels of sleep. Some users are highly active but do not get adequate sleep, such as user `7007744171` (65 minutes of sleep). 11 rows of data were filtered out due to NULL values contained in AvgDailySleepMinutes. 
- **Insight**: We can't assume with the current amount of data that highly active users may not be resting properly, but having a larger sample size may show potential in that assumption. It might be a common trend seen in smart device usage, where users may take off their smart device when sleeping resulting in not tracking sleep data.
  
### Activity vs. Heart Rate

![Steps vs. Heart Rate](https://github.com/taddybearrr/bellabeat-case-study/blob/cadef2c2dbdeadde264305944d968773c1d0c35b/visualizations/Average%20Heart%20Rate%20and%20Activity.pdf)

- **Observation**: Users with higher daily steps generally have lower heart rates, suggesting improved cardiovascular health. For example, users like `5553957443` (8,569 steps, 67.85 bpm) show signs of better fitness compared to less active users. 11 rows of data were filtered out due to NULL values contained in AvgHeartRate.
- **Insight**: Regular physical activity is linked to better heart health, but users may not be aware of how their fitness is improving over time.

### Sleep Quality and Heart Rate

![Sleep vs. Heart Rate](https://github.com/taddybearrr/bellabeat-case-study/blob/cadef2c2dbdeadde264305944d968773c1d0c35b/visualizations/Sleep%20Quality%20and%20Heart%20Rate.pdf)

- **Observation**: The correlation coefficient is approximately -0.28, indicating a weak negative correlation. Users who get more sleep tend to have lower heart rates. For instance, user `5577150313` (417 minutes of sleep, 67.63 bpm) shows better recovery compared to users who sleep less.
- **Insight**: More sleep may correlate with improved recovery, as reflected in lower heart rates. This suggests that Bellabeat should emphasize the importance of sleep in overall wellness.

### High-Activity Users

![High-Activity Users](./visualizations/Average_Sleep_and_Steps_by_User.pdf)

- **Observation**: High-activity users (over 10,000 steps) show varying sleep and heart rate patterns. User `4388161847` logs high steps and gets a decent amount of sleep, while user `7007744171` logs similar steps but gets very little sleep.
- **Insight**: Even highly active users may not be recovering properly. Bellabeat should help users find a balance between activity and rest for optimal health.

---

## Recommendations

Based on the analysis, here are the key recommendations for Bellabeat:

1. **Promote Recovery Features**: Highly active users often don't get enough sleep. Bellabeat should develop features that encourage recovery by suggesting rest days or providing **sleep optimization tips**.
   
2. **Track Heart Health Improvements**: Introduce features that allow users to track **heart rate improvements** over time, showing them how their fitness levels are improving with regular activity.

3. **Personalized Notifications**: Create personalized wellness notifications that highlight when users need more sleep or recovery time, especially for users with high activity and low sleep data.

4. **Segmented User Insights**: Offer **customized insights** based on user segments, such as “high-activity/low-sleep” users, and provide tailored recommendations that focus on their specific health needs.

---

## Conclusion

This case study provided insights into the relationship between user activity, sleep, and heart rate. The data suggests that while many users are active, they may not be optimizing their recovery, as reflected in inconsistent sleep and heart rate patterns. Bellabeat has the opportunity to enhance its product by focusing on **recovery, heart health tracking,** and **personalized recommendations**, which will provide greater value to users aiming to improve their overall wellness.

### Answers to the Key Questions:
1. **Trends in smart device usage**: Users primarily track activity and heart rate, with less emphasis on sleep and recovery.
2. **Application to Bellabeat customers**: Bellabeat can help its customers (tech-savvy women) understand their recovery patterns, encouraging them to prioritize sleep and heart health in addition to tracking activity.
3. **Influencing Bellabeat’s marketing strategy**: Bellabeat should emphasize **premium features** that focus on recovery, heart rate improvements, and personalized insights in their marketing campaigns, targeting **high-activity users** and wellness-conscious individuals.

For more information on the analysis process and data visualizations, please refer to the [analysis folder](./analysis/) and [visualizations folder](./visualizations/).
