## SQL Request
### Merging the tables
CREATE TABLE `case-stud-1-bike-trip.Bike_trip.cyclistic_data_2023_05_2024_04` AS (   
&nbsp;&nbsp;&nbsp;&nbsp;SELECT * FROM `case-stud-1-bike-trip.Bike_trip.Trip_data_05_2023`  
&nbsp;&nbsp;&nbsp;&nbsp;UNION ALL  
&nbsp;&nbsp;&nbsp;&nbsp;SELECT * FROM `case-stud-1-bike-trip.Bike_trip.Trip_data_06_2023`  
&nbsp;&nbsp;&nbsp;&nbsp;UNION ALL  
&nbsp;&nbsp;&nbsp;&nbsp;SELECT * FROM `case-stud-1-bike-trip.Bike_trip.Trip_data_07_2023`  
&nbsp;&nbsp;&nbsp;&nbsp;UNION ALL  
&nbsp;&nbsp;&nbsp;&nbsp;SELECT * FROM `case-stud-1-bike-trip.Bike_trip.Trip_data_08_2023`  
&nbsp;&nbsp;&nbsp;&nbsp;UNION ALL  
&nbsp;&nbsp;&nbsp;&nbsp;SELECT * FROM `case-stud-1-bike-trip.Bike_trip.Trip_data_09_2023`  
&nbsp;&nbsp;&nbsp;&nbsp;UNION ALL  
&nbsp;&nbsp;&nbsp;&nbsp;SELECT * FROM `case-stud-1-bike-trip.Bike_trip.Trip_data_10_2023`  
&nbsp;&nbsp;&nbsp;&nbsp;UNION ALL  
&nbsp;&nbsp;&nbsp;&nbsp;SELECT * FROM `case-stud-1-bike-trip.Bike_trip.Trip_data_11_2023`  
&nbsp;&nbsp;&nbsp;&nbsp;UNION ALL  
&nbsp;&nbsp;&nbsp;&nbsp;SELECT * FROM `case-stud-1-bike-trip.Bike_trip.Trip_data_12_2023`  
&nbsp;&nbsp;&nbsp;&nbsp;UNION ALL  
&nbsp;&nbsp;&nbsp;&nbsp;SELECT * FROM `case-stud-1-bike-trip.Bike_trip.Trip_data_01_2024`  
&nbsp;&nbsp;&nbsp;&nbsp;UNION ALL  
&nbsp;&nbsp;&nbsp;&nbsp;SELECT * FROM `case-stud-1-bike-trip.Bike_trip.Trip_data_02_2024`  
&nbsp;&nbsp;&nbsp;&nbsp;UNION ALL  
&nbsp;&nbsp;&nbsp;&nbsp;SELECT * FROM `case-stud-1-bike-trip.Bike_trip.Trip_data_03_2024`  
&nbsp;&nbsp;&nbsp;&nbsp;UNION ALL  
&nbsp;&nbsp;&nbsp;&nbsp;SELECT * FROM `case-stud-1-bike-trip.Bike_trip.Trip_data_04_2024`  
)  
### Check the ride duration
SELECT  
&nbsp;&nbsp;&nbsp;&nbsp;ride_id, started_at, ended_at,  
&nbsp;&nbsp;&nbsp;&nbsp;TIMESTAMP_DIFF(ended_at, started_at, MINUTE)  
FROM `case-stud-1-bike-trip.Bike_trip.cyclistic_data_2023_05_2024_04`  
WHERE  
&nbsp;&nbsp;&nbsp;&nbsp;TIMESTAMP_DIFF(ended_at, started_at, MINUTE) <= 1 OR  
&nbsp;&nbsp;&nbsp;&nbsp;TIMESTAMP_DIFF(ended_at, started_at, MINUTE) >= 1440  
### Delete duration inconsistencies
DELETE
FROM `case-stud-1-bike-trip.Bike_trip.cyclistic_data_2023_05_2024_04` 
WHERE 
&nbsp;&nbsp;&nbsp;&nbsp;TIMESTAMP_DIFF(ended_at, started_at, MINUTE) <= 1 OR
&nbsp;&nbsp;&nbsp;&nbsp;TIMESTAMP_DIFF(ended_at, started_at, MINUTE) >= 1440
### Create the table with the data cleaned and the timestamp column divide in year, month and day column, and create a trip duration column.
SELECT  
&nbsp;&nbsp;&nbsp;&nbsp;ride_id,  
&nbsp;&nbsp;&nbsp;&nbsp;rideable_type,  
&nbsp;&nbsp;&nbsp;&nbsp;started_at,  
&nbsp;&nbsp;&nbsp;&nbsp;ended_at,  
&nbsp;&nbsp;&nbsp;&nbsp;TIMESTAMP_DIFF(ended_at, started_at, MINUTE) AS ride_length_in_mins,  
&nbsp;&nbsp;&nbsp;&nbsp;CASE  
&nbsp;&nbsp;&nbsp;&nbsp;EXTRACT(YEAR FROM started_at)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;WHEN 2023 THEN '2023'  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;WHEN 2024 THEN '2024'  
&nbsp;&nbsp;&nbsp;&nbsp;END AS year,  
&nbsp;&nbsp;&nbsp;&nbsp;CASE  
&nbsp;&nbsp;&nbsp;&nbsp;EXTRACT(MONTH FROM started_at)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;WHEN 1 THEN 'January'  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;WHEN 2 THEN 'February'  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;WHEN 3 THEN 'March'  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;WHEN 4 THEN 'April'  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;WHEN 5 THEN 'May'    
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;WHEN 6 THEN 'June'  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;WHEN 7 THEN 'July'  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;WHEN 8 THEN 'August'  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;WHEN 9 THEN 'September'  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;WHEN 10 THEN 'October'     
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;WHEN 11 THEN 'November'  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;WHEN 12 THEN 'December'  
&nbsp;&nbsp;&nbsp;&nbsp;END AS month,  
&nbsp;&nbsp;&nbsp;&nbsp;CASE EXTRACT(DAYOFWEEK FROM started_at)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;WHEN 1 THEN 'Sunday'  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;WHEN 2 THEN 'Monday'  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;WHEN 3 THEN 'Tuesday'  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;WHEN 4 THEN 'Wednesday'  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;WHEN 5 THEN 'Thursday'  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;WHEN 6 THEN 'Friday'  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;WHEN 7 THEN 'Saturday'     
&nbsp;&nbsp;&nbsp;&nbsp;END AS day_of_week,  
&nbsp;&nbsp;&nbsp;&nbsp;start_station_name,  
&nbsp;&nbsp;&nbsp;&nbsp;start_station_id,  
&nbsp;&nbsp;&nbsp;&nbsp;end_station_name,  
&nbsp;&nbsp;&nbsp;&nbsp;end_station_id,  
&nbsp;&nbsp;&nbsp;&nbsp;start_lat,  
&nbsp;&nbsp;&nbsp;&nbsp;start_lng,  
&nbsp;&nbsp;&nbsp;&nbsp;end_lat,  
&nbsp;&nbsp;&nbsp;&nbsp;end_lng,  
&nbsp;&nbsp;&nbsp;&nbsp;member_casual  
FROM `case-stud-1-bike-trip.Bike_trip.cyclistic_data_2023_05_2024_04`  
### Calcul average duration
SELECT  
&nbsp;&nbsp;&nbsp;&nbsp;member_casual, rideable_type,  
&nbsp;&nbsp;&nbsp;&nbsp;ROUND(AVG(ride_length_in_mins),2) AS avg_duration  
FROM `case-stud-1-bike-trip.Bike_trip.cyclistic_data_cleaned`  
GROUP BY member_casual, rideable_type  
ORDER BY member_casual, rideable_type  
### Calcul average duration depend of the day
SELECT member_casual, day_of_week,  
&nbsp;&nbsp;&nbsp;&nbsp;AVG(ride_length_in_mins) AS avg_ride_length,  
FROM `case-stud-1-bike-trip.Bike_trip.cyclistic_data_cleaned`  
GROUP BY member_casual, day_of_week  
ORDER BY member_casual  

### Calcul minimum and maximum duration
SELECT  
&nbsp;&nbsp;&nbsp;&nbsp;member_casual,  
&nbsp;&nbsp;&nbsp;&nbsp;MIN(ride_length_in_mins) AS min_trip_duration,  
&nbsp;&nbsp;&nbsp;&nbsp;MAX(ride_length_in_mins) AS max_trip_duration  
FROM `case-stud-1-bike-trip.Bike_trip.cyclistic_data_cleaned`  
GROUP BY member_casual  

### Calcul the month popularity
SELECT  
&nbsp;&nbsp;&nbsp;&nbsp;member_casual, month,  
&nbsp;&nbsp;&nbsp;&nbsp;COUNT(*) AS total_ride  
FROM `case-stud-1-bike-trip.Bike_trip.cyclistic_data_cleaned`  
GROUP BY member_casual, month  
ORDER BY total_ride, member_casual, month DESC  

### Calcul the hour popularity
SELECT member_casual,  
&nbsp;&nbsp;&nbsp;&nbsp;EXTRACT(HOUR FROM started_at) AS hour_of_day,  
&nbsp;&nbsp;&nbsp;&nbsp;COUNT(*) AS total_trips  
FROM `case-stud-1-bike-trip.Bike_trip.cyclistic_data_cleaned`  
GROUP BY member_casual,hour_of_day  
ORDER BY total_trips DESC  

### Calcul the type of bike popularity
SELECT  
&nbsp;&nbsp;&nbsp;&nbsp;member_casual, rideable_type,  
&nbsp;&nbsp;&nbsp;&nbsp;COUNT(*) AS total_ride  
FROM `case-stud-1-bike-trip.Bike_trip.cyclistic_data_cleaned`  
GROUP BY member_casual, rideable_type  
ORDER BY member_casual, rideable_type  
