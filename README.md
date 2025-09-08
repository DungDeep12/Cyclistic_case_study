# Google Data Analytics Capstone: Cyclistic Bike-Share Analysis Case Study
## Welcome
Welcome to the Cyclistic bike-share analysis case study! In this case study, you work for a fictional company, Cyclistic, along with some key team members. In order to answer the business questions, follow the steps of the data analysis process: Ask, Prepare, Process, Analyze, Share, and Act. Along the way, the Case Study Roadmap tables — including guiding questions and key tasks — will help you stay on the right path.
## Scenario
You are a junior data analyst working on the marketing analyst team at Cyclistic, a bike-share company in Chicago. The director of marketing believes the company’s future success depends on maximizing the number of annual memberships. Therefore, your team wants to understand how casual riders and annual members use Cyclistic bikes differently. From these insights, your team will design a new marketing strategy to convert casual riders into annual members. But first, Cyclistic executives must approve your recommendations, so they must be backed up with compelling data insights and professional data visualizations.
## Characters and Teams
* **Cyclistic**: A bike-share program that features more than 5,800 bicycles and 600 docking stations. Cyclistic sets itself apart by also offering reclining bikes, hand tricycles, and cargo bikes, making bike-share more inclusive to people with disabilities and riders who can’t use a standard two-wheeled bike. The majority of riders opt for traditional bikes; about 8% of riders use the assistive options. Cyclistic users are more likely to ride for leisure, but about 30% use the bikes to commute to work each day.
*	**Lily Moreno**: The director of marketing and your manager. Moreno is responsible for the development of campaigns and initiatives to promote the bike-share program. These may include email, social media, and other channels.
*	**Cyclistic marketing analytics team**: A team of data analysts who are responsible for collecting, analyzing, and reporting data that helps guide Cyclistic marketing strategy. You joined this team six months ago and have been busy learning about Cyclistic’s mission and business goals—as well as how you, as a junior data analyst, can help Cyclistic achieve them.
*	**Cyclistic executive team**: The notoriously detail-oriented executive team will decide whether to approve the recommended marketing program.
## About the Company
In 2016, Cyclistic launched a successful bike-share offering. Since then, the program has grown to a fleet of 5,824 bicycles that are geotracked and locked into a network of 692 stations across Chicago. The bikes can be unlocked from one station and returned to any other station in the system anytime.

Until now, Cyclistic’s marketing strategy relied on building general awareness and appealing to broad consumer segments. One approach that helped make these things possible was the flexibility of its pricing plans: single-ride passes, full-day passes, and annual memberships. Customers who purchase single-ride or full-day passes are referred to as casual riders. Customers who purchase annual memberships are Cyclistic members.

Cyclistic’s finance analysts have concluded that annual members are much more profitable than casual riders. Although the pricing flexibility helps Cyclistic attract more customers, Moreno believes that maximizing the number of annual members will be key to future growth. Rather than creating a marketing campaign that targets all-new customers, Moreno believes there is a solid opportunity to convert casual riders into members. She notes that casual riders are already aware of the Cyclistic program and have chosen Cyclistic for their mobility needs.

Moreno has set a clear goal: Design marketing strategies aimed at converting casual riders into annual members. In order to do that, however, the team needs to better understand how annual members and casual riders differ, why casual riders would buy a membership, and how digital media could affect their marketing tactics. Moreno and her team are interested in analyzing the Cyclistic historical bike trip data to identify trends.
## Phase 1 – ASK
Three questions will guide the future marketing program:
1.	How do annual members and casual riders use Cyclistic bikes differently?
2.	Why would casual riders buy Cyclistic annual memberships?
3.	How can Cyclistic use digital media to influence casual riders to become members?

Moreno has assigned you the first question to answer: **How do annual members and casual riders use Cyclistic bikes differently?**
### Stakeholders
*	**Lily Moreno**: Director of Marketing
*	**Marketing Analytics Team**
*	**Cyclistic Executive Team**
### Business Task
Analyze data to gain insights into how users use Cyclistic's bikes differently by membership type and to identify trends based on Cyclistic's marketing strategy.
## Phase 2 – PREPARE
The dataset I use is available from the link below:

[The previous 12 months of Cyclistic trip data](https://divvy-tripdata.s3.amazonaws.com/index.html)

Are there issues with bias or credibility in this data? Does your data ROCCC?
*	**Reliable**: Data comes from a reputable source (Motivate International Inc.).
*	**Original**: This is primary data directly from Cyclistic’s operations, not from a third party.
*	**Comprehensive**: It covers full features for providing a complete picture of usage patterns.
*	**Current**: The 4 quarterly datasets from 2019 may be enough to reflect relevant trends.
*	**Cited**: The data is publicly available under a license from Motivate International Inc.
*	**Bias Concern**: The data may underrepresent certain groups, such as cash versus digital payments or variations across geographic regions.

For this analysis, I used **Python** to explore the data.

You can find the datasets I used and the full notebook [here](https://colab.research.google.com/drive/1LE2j1g_MxgIbKgxDdieDVqAavwOtQfQe?usp=sharing)
### Dataset Overview
All 4 quarterly datasets consists of 3,818,004 rows and covers trips recorded from January 1, 2019, to December 31, 2019. It includes 12 columns with details about each trip:
*	**trip_id**: Unique identifier for each trip
*	**start_time**: Date and time when the trip started
*	**end_time**: Date and time when the trip ended
*	**bikeid**: Unique identifier for the bike used
*	**tripduration**: Total duration of the trip
*	**from_station_id**: ID of the station where the trip started
*	**from_station_name**: Name of the station where the trip started
*	**to_station_id**: ID of the station where the trip ended
*	**to_station_name**: Name of the station where the trip ended
*	**usertype**: User type (Subscriber or Customer)
*	**gender**: User's gender (if available)
*	**birthyear**: User's birth year (if available)
### Data Cleaning Process
1. **Rename Columns** – Make column names consistent across all datasets.
3.	**Convert Data Types** – Remove commas and convert tripduration to numbers.
4.	**Fill Missing Values**
    * **Gender**: Fill missing values based on the male-to-female ratio.
    * **Birth Year**: Fill missing values using the median based on user type and quarter.
5.	**Add New Columns**
    * **Age**: Calculate by subtracting birth year from 2020
  	 * **Day_of_week**: Extract from start_time to show the day of the week
  	 * **Age Group**: Categorize users into age groups.
5.	**Merge Data** – Combine all four quarterly datasets into one.
## Analyze
In this section, we analyze how annual members (subscribers) and casual riders (customers) use the bike-share service differently. By examining Trip Frequency and Volume, Trip Duration, Station Usage patterns, Time of Use (Temporal Pattern), Demographic Distributions, and key differences, we aim to provide actionable insights for designing targeted marketing strategies.
### Trip Frequency and Duration
To better understand how annual members and casual riders differ, we first explored ride frequency and trip duration

**Graph 1: Total Trips by User Type**
![image alt](https://github.com/DungDeep12/Cyclistic_case_study/blob/main/Visualization/total_trips_by_usertype.png?raw=true)

The number of trips for Subscriber are three time higher than Customer

**Graph 2: Monthly Trip Trend by User Type**
![image alt](https://github.com/DungDeep12/Cyclistic_case_study/blob/main/Visualization/monthly_trip_trends.png?raw=true)

Both customers and subscribers follow similar seasonal trends, with ride counts peaking from May to September

**Graph 3: Trip Duration Distribution by User Type**
![image alt](https://github.com/DungDeep12/Cyclistic_case_study/blob/main/Visualization/trip_duration_distribution.png?raw=true)

Most of the Subscriber’s Trips are below 30 minutes while Customer’ Trips took 10 to 30 minutes or even above 30 minutes

**Graph 4: Average Trip Duration by hour of Day**
![image alt](https://github.com/DungDeep12/Cyclistic_case_study/blob/main/Visualization/duration_by_hour.png?raw=true)

Customers have higher average Trip Duration, especially in the morning around 3 am to 5 am.

**Graph 5: Average Trip Duration by Day of Week**
![image alt](https://github.com/DungDeep12/Cyclistic_case_study/blob/main/Visualization/duration_by_day.png?raw=true)

The same applies to Day of Week with Customer also have higher average Trip Duration.

Combine all of the information above we have some **Key Insights**:
* Customers take longer trips on average, suggesting they may use bikes for leisure or tourism rather than routine travel.
* Both user types ride more frequently during warmer months, indicating a seasonal influence on bike usage.
### Time of Use (Temporal Patterns) Analysis

Next, we analyze time data to identify when each user type uses bikes

**Graph 6: Trip Count by hour of day**
![image alt](https://github.com/DungDeep12/Cyclistic_case_study/blob/main/Visualization/hourly_trip_counts.png?raw=true)

**Graph 7: Trip Count by Day of Week**
![image alt](https://github.com/DungDeep12/Cyclistic_case_study/blob/main/Visualization/daily_trip_counts.png?raw=true)

**Key insight:**
* Subscribers ride more consistently throughout the week peaking around morning (6 am to 9 am) and evening (3 pm to 7 pm)
* Customers, on the other hand, use bikes a lot more at the weekend, around afternoon and evening (from 12 pm to 7 pm)
### Station Usage (Spatial Patterns)
We analyzed station data to Understand where each user type starts and ends their trips.

**Graph 8: Top 10 Start Station**
![image alt](https://github.com/DungDeep12/Cyclistic_case_study/blob/main/Visualization/top_start_stations.png?raw=true)

**Graph 9: Top 10 End Station**
![image alt](https://github.com/DungDeep12/Cyclistic_case_study/blob/main/Visualization/top_end_stations.png?raw=true)

**Graph 10: Top 10 Start and End Station**
![image alt](https://github.com/DungDeep12/Cyclistic_case_study/blob/main/Visualization/top_stations_overall.png?raw=true)

**Graph 11: Round Trips vs One-Way Trips**
![image alt](https://github.com/DungDeep12/Cyclistic_case_study/blob/main/Visualization/round_vs_oneway_trips.png?raw=true)

**Key insight:**
* Both Customer and Subscriber prefer to have One-Way trips with Subscriber is three time higher than Customer.
* Customers show a clear spike in rides at popular stations like Streeter Dr & Grand Ave, Millennium Park and Lake Shore Dr & Monroe St, which are tourist hotspots.
* Subscribers, on the other hand, show higher usage at stations likely tied to commuting routes (e.g., Canal St & Adam St, Clinton St, …).
### Demographic Analysis
We examined gender and age distributions to uncover demographic differences between customers and subscribers.

**Gender Distribution**

**Graph 12: Pie Charts Showing Gender Distribution for Subscribers and Customers**
![image alt](https://github.com/DungDeep12/Cyclistic_case_study/blob/main/Visualization/gender_distribution.png?raw=true)

**Key Insights:**
* The proportion of female subscribers is 7% lower than that of female customers.
* This indicates that women are less likely to opt for annual memberships, possibly due to differing usage preferences or limited marketing appeal.

**Age Distribution**

**Graph 13: Pie Chart Showing Age Distribution of Customers and Subscribers**
![image alt](https://github.com/DungDeep12/Cyclistic_case_study/blob/main/Visualization/age_distribution.png?raw=true)

**Key Insights:**
* The 26-35 age group dominates both user types, but it’s more pronounced among customers (81%) compared to subscribers (50.5%).
* Riders aged 36 and older are more likely to be subscribers than customers.

Younger riders (26-35) appear more inclined to use bikes casually, while older riders (36+) prefer subscriptions, possibly reflecting more established commuting habits.

### Comparison of Customers vs. Subscribers
The table below summarizes the key differences between customers and subscribers based on the analysis:

|**Category**|**Customers**|**Subscribers**|
|------------|-------------|---------------|
|**Trip Duration**|Longer average trip durations|Shorter average trip durations|
|**Ride Frequency**|More rides on weekends|Consistent rides throughout the week|
|**Seasonal Usage**|Peaks in Summer and Fall|Peaks in Summer and Fall|
|**Station Usage**|High usage at tourist-heavy stations (e.g., Millennium Park)|High usage at commuting-related stations (e.g., Canal St & Adam St)|
|**Gender Distribution**|Higher proportion of females|Lower proportion of females|
|**Age Distribution**|Predominantly 26-35 years old (81%)|More evenly distributed, higher proportion of 36+ years old (50.5% in 26-35 group)|

**Key Insights:**
* Customers are more likely to use Cyclistic’s bikes for leisure or tourism, as evidenced by longer trips, weekend spikes, and activity at tourist-friendly stations.
* Subscribers demonstrate a pattern of regular, utilitarian use, with shorter, more frequent trips throughout the week and a broader age range, suggesting commuting or daily exercises.
### Conclusion
This analysis highlights distinct usage patterns between annual members and casual riders. Customers lean toward recreational use, influenced by weather and weekend availability, while subscribers exhibit consistent, practical usage tied to routines like commuting. These insights provide a foundation for crafting marketing strategies to convert casual riders into annual members by addressing their specific needs and preferences.
## Share & Act
I used Tableau to recreate graphs, you can view it [here](https://public.tableau.com/app/profile/nguyen.dung6560/viz/CyclisticDashboard_17547474792690/Dashboard1) or from the [PDF](https://github.com/DungDeep12/Cyclistic_case_study/blob/main/Cyclistic%20DashBoard.pdf) version.
### Recommendations
**1. Annual Plan for Weekday Commuters: Annual subscription with unlimited weekday rides for commuters**
   * **Problem Solved:** Subscribers ride more on weekdays, indicating commuting patterns. This plan encourages casual riders who commute to switch from single-ride or day passes to annual memberships 
**2. Annual Plan for Summer & Autumn Only: Seasonal subscription for Q2 and Q3, priced lower than full-year plans.**
   * **Problem Solved:** Targets casual riders active in warmer months (Summer, Fall)
**3. Plan Only for Weekends: Unlimited weekend rides with discounts for longer trips.**
   * **Problem Solved:** Casual riders predominantly use bikes on weekends at tourist-heavy stations like Millennium Park. This plan targets their recreational habits, making membership more attractive without a full-week commitment.
**4. Discounts for Women on Special Days: Offer subscription discounts on days like International Women’s Day, promoted through targeted digital campaigns.**
   * **Problem Solved:** Addresses 7% lower female subscriber proportion.
