# Bike Sharing Dashboard

An interactive Bike Sharing Analytics Dashboard built using
Microsoft Power BI. The project explores bike activity,
station popularity, bike utilization, trip duration, and user behaviour
through interactive visualizations and KPI cards.

Dashboard Overview
The dashboard contains four analytical sections/pages:
1. Bike Sharing Overview -- overall trip KPIs, Cards, monthly trips, trips
   by day, popular starting and ending stations, and member versus
   short-term trips.
2. Station & Trip Duration Analysis -- trips by end station,
   average duration by user type, and average trip duration by month.
3. User & Bike Analysis -- trips by user type, most-used bike IDs,
   and trips by hour of day.
4. Key Performance Summary -- highest and lowest trip years/months,
   bike usage, user-type duration comparisons, and popular/less-popular
   stations.

  
Dataset Description
The project analyzes bike-sharing trip records containing information
such as:
- Start date/time and end date/time
- Starting station and ending station
- Bike ID / bike number
- Trip duration
- User type
The dashboard displays approximately 50,000 trips, 476 unique
bikes, 50 starting stations, and 51 ending stations. The
displayed date range is 11 January 2014 to 4 December 2015.

Objectives
- Analyze overall bike-sharing demand.
- Identify popular starting and ending stations.
- Explore trip patterns by month, day of week, and hour.
- Compare usage by user type.
- Measure average trip duration.
- Identify frequently used bikes.
- Present insights through an interactive Power BI dashboard.
  
Data Preparation
The data preparation and modeling workflow includes:
- Checking and assigning appropriate data types.
- Creating a date-only field from the trip start timestamp.
- Extracting the hour, weekday name, and month name.
- Converting trip duration from seconds to minutes.
- Creating a calendar table for date-based analysis.
- Creating a relationship between the calendar date and the date-only
  trip field.
- Sorting month and weekday labels by their numeric order where
  required.
  
Data Model
The model uses the trip table as the main fact table and a separate
DateTable for calendar-based analysis.

Main trip table: trip records, timestamps, station details, bike
details, user type, and trip duration.

Date table: date, year, month name, month number, day name, day
number, and quarter.

DAX Examples

Total Trips = COUNTROWS('trip')

Unique Bikes =
DISTINCTCOUNT('trip'[Bike number])

Average Duration =
AVERAGE('trip'[Trip_Duration_Minutes])

Trip_Duration_Minutes =
'trip'[tripduration] / 60

Trip_Hour =
HOUR('trip'[starttime])

Trip_Date =
DATE(
    YEAR('trip'[starttime]),
    MONTH('trip'[starttime]),
    DAY('trip'[starttime])
)

Month_Name =
FORMAT('trip'[Trip_Date], "MMMM")

Day_Name =
FORMAT('trip'[Trip_Date], "dddd")


Trip_Duration_Minutes, Trip_Hour, Trip_Date, Month_Name, and
Day_Name are calculated columns; Total Trips, Unique Bikes,
Average Duration are measures. Ensure the
duration source column is in seconds before dividing by 60.

Key Findings
Based on the dashboard:
- Approximately 50,000 trips are represented.
- The dashboard reports 476 unique bikes.
- The overall average trip duration is approximately 17.75
  minutes.
- Members account for 34,811 trips (about 69.6%).
- Short-Term Pass Holders account for 15,189 trips (about 30.4%).
- October 2014 is the highest month in 2014, with 7,148 trips.
- March 2015 is the highest month in 2015, with 6,907 trips.
- The most popular starting station is REI / Yale Ave N & John St,
  with 1,959 trips.
- The most popular ending station is 2nd Ave & Pine St, with
  2,344 trips.
- Bike SEA00390 is the most-used bike shown, with 187 trips.
- Average trip duration is 10.08 minutes for Members and 35.33
  minutes for Short-Term Pass Holders.
- The hourly chart shows its highest displayed activity around 8
  PM.
  

Tools & Technologies
- Microsoft Power BI Desktop
- Power Query
- DAX (Data Analysis Expressions)
- CSV data files

How to View the Project
1. Download or clone this repository.
2. Open dashboard/Bike_Sharing_Dashboard.pbix using Power BI
   Desktop.
3. If prompted, update the data source paths to point to your local
   dataset files.
4. Refresh the data if the source files are available.
5. Explore the report pages and use the slicers to filter the
   dashboard.
   
Conclusion
This project demonstrates how Power BI can be used to transform
bike-sharing trip data into an interactive analytical dashboard. It
highlights demand patterns, station popularity, bike usage, and
differences in trip duration across user categories. The dashboard
provides a foundation for understanding bike-sharing operations and
supporting data-informed decisions.

Author
Student Name: Devesh Saxena
Registration Number: PIET24CD025
