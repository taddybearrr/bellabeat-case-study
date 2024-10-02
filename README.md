# Bellabeat Data Analysis Case Study

This project is a data analysis case study for Bellabeat, a high-tech company focused on women's health and wellness. The goal is to analyze user activity, sleep, and heart rate data to generate insights and actionable recommendations to improve Bellabeat's product features.

## Table of Contents
1. [Project Overview](#project-overview)
2. [Data Sources](#data-sources)
3. [Analysis](#analysis)
4. [Visualizations](#visualizations)
5. [Key Insights and Recommendations](#key-insights-and-recommendations)
6. [Conclusions](#conclusions)

## Project Overview
This case study explores Bellabeat's user data from April and May 2016, focusing on the relationship between user activity (steps), sleep, and heart rate. The goal is to identify key trends and provide actionable recommendations for improving Bellabeat's product features, particularly regarding recovery and cardiovascular health.

## Data Sources
The data used for this analysis comes from a public dataset on Kaggle:
https://www.kaggle.com/datasets/arashnic/fitbit.

## Analysis
The analysis used SQL queries in Google BigQuery to clean, aggregate, and explore the data. Key analyses include:
- **Activity vs. Sleep**: Understanding how user activity affects sleep duration.
- **Activity vs. Heart Rate**: Investigating the relationship between daily steps and heart rate.
- **Sleep Quality and Heart Rate**: Exploring how sleep duration correlates with heart rate, indicating recovery.

## Visualizations
The following visualizations were created on Google Sheet's "Chart" feature to illustrate key trends:
- [Steps vs. Sleep](./visualizations/steps_vs_sleep.png)
- [Steps vs. Heart Rate](./visualizations/steps_vs_heart_rate.png)
- [Sleep vs. Heart Rate](./visualizations/sleep_vs_heart_rate.png)

## Key Insights and Recommendations
- **Insight 1**: Users with higher daily steps don’t necessarily get more sleep. Bellabeat should introduce features to encourage recovery in highly active users.
- **Insight 2**: Higher activity levels generally correlate with lower heart rates, indicating fitness. Bellabeat could implement a heart rate tracking feature that provides insights into cardiovascular health improvements.
- **Insight 3**: A strong correlation between longer sleep and lower heart rates suggests better recovery. Bellabeat could emphasize the importance of sleep for heart health and offer personalized sleep recommendations.

## Conclusions
This case study identified several key areas where Bellabeat could improve its product offering by focusing on user recovery, heart health, and personalized recommendations based on activity and sleep data.

For a detailed walkthrough of the SQL queries and data cleaning process, please refer to the [analysis folder](./analysis/).
