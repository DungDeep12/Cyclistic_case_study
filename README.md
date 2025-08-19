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
