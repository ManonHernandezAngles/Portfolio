## Cyclistic Cappstone Project
### Introduction
This is the case study of the Google Data Analytics certificate. In this project I will follow the steps taught in the course: Ask, Prepare, Process, Analyze, Share and Act.
### Project Background
This project follows a scenario in which  I am working as a junior data analyst on the marketing team at Cyclistic. 
Cyclistic is an imaginary bike-share company with 5,824 bicycles and 692 docking stations. 
A bike can be unlocked from one station and returned to any other station in the system anytime. 
Until now the marketing strategy was built on a large pane of customers and general awareness. 
The flexibility of the pricing plans helps for this strategy. 
For now, the pricing plan consists of three offers: single-ride, full-day passes, and annual memberships.
Customers purchasing single-ride or full-day passes are referred to as casual riders and customers purchasing annual memberships are Cyclistic members. Cyclistic’s finance analysts have concluded that annual members are much more profitable than casual riders. The director of marketing thinks maximizing the number of annual members is the key to annual growth. The team wants to understand how casual riders and annual members use the service differently. The director of marketing wants to convert casual riders into annual members. In this case study, we want to design a new marketing strategy to convert casual riders into annual members.
### Ask
Three cornerstone questions guide the making of the future marketing program:
- How do annual members and casual riders use Cyclistic bikes differently?
- Why would casual riders buy Cyclistic annual memberships? 
- How can Cyclistic use digital media to influence casual riders to become members? 
The first problem we are trying to solve is how to convert casual riders into annual members. For that, we need to understand how differently both usertype use the bikes. The insights are going to help us build a solid marketing strategy for the annual growth.
The key stakeholders are the marketing analytics team and the director of marketing after that the executive team are also important because we need to present them the strategy for insight validation.
### Prepare
The original data are located in the aws cloud (on this link : https://divvy-tripdata.s3.amazonaws.com/index.html) and are protected with the following license https://divvybikes.com/data-license-agreement. As long as the data remains anonymous and the original source is not altered, it is possible to work with this data while respecting privacy and security conditions. This data is organized in files by month or by quarter depending on the year, for our period it is divided in month files. This data set does not have issues with bias or credibility as they are collected by a credible company. It has been updated every month since 2013 with the same anonymisation process. 
The data follow the ROCCC representation:
- **Reliable** - High – The data are provided by a company.
- **Original** – High- The data are securitized and the source can’t be modified.
- **Comprehensive** – High – There are many rows and only a small percentage of missing data.
- **Current** – High - The data are updated every month.
- **Cited** – We know how and when the data are collected.
For this analysis we are going to use SQL for the cleaning and analyzing phase and Tableau for visualization.
### Process
The first step is merging the tables.
This table has 5 738 612 rows and 13 columns.  
![Table_column](https://github.com/user-attachments/assets/71a93935-db35-4986-bf11-4ee2eed55891)  
After that we check the null value, we have null value only on the start_name, start_id, end_name, end_id, end_lat, end_lng.  
Then we check each column from the left to the right to determine the data type and uncover missing values, outliers, inconsistencies and errors.  
The ride_id column is uniform, in the rideable_type we have only three results remaining: electric, classic and docked so it is correct. After that we check the ride duration, we have 257 483 rows with duration less than one minute or more than 24 hours. For the start_station_name column we have 885 429 null values and for the end_station_name column we have 939 115 null values. The start_station_id and end_station_id columns are inconsistent or null values.We do not need these columns for the analysis. On the latitudes and longitudes columns we have 7610 null values. And on the member_casual columns we have two types of data and no null value.  
Delete the null value for start_station_name and end_station_name 1 402 657 rows deleted.  
Delete duration inconsistencies, 154 471 rows deleted.  
We divide the timestamp column in year month and day column and create a trip duration column.  
At the end we have a cleaned data table with 4 181 484 rows and 17 columns.  
### Analyze
First we have to analyze the table with SQL. Then we import the table in Tableau to visualize and discover more trends and relationships.  
Cyclistic members recorded greater bicycle activity than casual riders. Members represent 65% (2 699 228) and casual riders represent 35% (1 482 256).  
Casual members prefer using classic bicycles over electric bicycles. Additionally, docked bicycles are exclusively used by casual members.  
The average ride length is longer for casual riders with 23,35 minutes when the members average ride length is 12,33 minutes. The ride duration of Cyclistic members are approximately two times shorter than casual riders.  
Both usertype have the lowest activity in January 2024, 17 108 rides for casual riders and 90 781 rides for Cyclistic members. Members have the highest activity in August 2023 (337 985 rides), and the casual rider in July 2023 (238 255 rides).  
The monthly average ride duration for Cyclistic members is the highest in August 2023 (13,27 minutes). For casual riders the highest average ride duration is in July 2023 (25,35 minutes).  
Commonly the Cyclistic members use the bike more during business days and the casual riders during the week-end. The highest day for casual riders is Saturday (304 856 rides) and for members is Tuesday (436 287 rides).  
Both of the usertype have the longest average ride duration on Sunday, 27,29 minutes for casual riders and 13,92 minutes for Cyclistic members.  
During the day, casual riders use the bike most at 5p.m. (145 321 rides). For Cyclistic members we see two preferred times. The first being 8a.m. (189 556 ride) and the second, 5p.m. (294 642 rides).  
### Share
![Dashboard 4](https://github.com/user-attachments/assets/76c64eb1-ff91-4dc6-92a4-fff266311dac)
#### Similarity
Both Cyclistic members and casual riders use the bike more in spring and summer, the number of rides decreases in September, it is probably a consequence of the decrease in temperatures, it is a less comfortable ride during autumn or winter.  
They both have an average ride duration during week-end, and they both ride more at the end of the day.  
Both Cyclistic members and casual riders prefer using classic bicycles over electric bicycles. Notably, docked bicycles are only used by casual members.  
The minimum and maximum duration for classic bike rides are very similar for each usertype, the minimum trip duration is two minutes for both users and the maximum trip duration is 1439 minutes (almost 24 hours) for cyclistic members and 1437 minutes (almost 24 hours) for casual riders.  
#### Differences
The cyclistic members have an average ride duration two times shorter than casual riders.  
The average ride duration by month is stable for Cyclistic members, while casual riders experience an increase in ride duration from April to August.  
The Cyclistic members use the bike more during business days while casual riders use more during week-end.  
### Act
Cyclistic  could create a monthly subscription plan with a discount when purchasing six months to create opportunity between day pass and annual subscription. Users could choose their preferred membership according to their own needs. Some riders do not need an annual membership but could be interested in a monthly or six-month membership. Cyclistic  can also propose sponsorship, when a user introduces a friend or family member to the company services they could receive an additional discount.  
Cyclistic could set-up seasonal campaigns.They could offer a limited-time discount for members to encourage casual riders to take a membership, particularly during the winter when the service is less used, to boost usage.  
We can organize events for members, like group rides or challenges. This  approach aims to increase the number of rides but also encourages casual riders to join a membership program to access these events.  
Those opportunities need to be shared with the target audience  on social media for increased popularity. SEO and increased visibility will definitely  help touch a larger potential user base and thus create  more members.
