# Google-Data-Analytics-Capstone

## Overview

This case study was done for the Google Data Analytics Professional Certificate program on Coursera. It details my findings for track A case study 1, "How does a bike-share navigate speedy success". In this study, I am a junior data analyst working on the marketing analytics team at Cyclistic, a fictional bike-share company in Chicago.The director of marketing believes the company’s future success depends on maximizing the number of annual memberships. Therefore, my team wants to understand how casual riders and annual members use Cyclistic bikes differently. From these insights, my team will design a new marketing strategy to convert casual riders into annual
members. But first, Cyclistic executives must approve my recommendations, so they must be backed up with compelling data insights and professional data visualizations. The following deliverable requirements are listed in the instructions:

1. A clear statement of the business task
2. A description of all data sources used
3. Documentation of any cleaning or manipulation of data
4. A summary of your analysis
5. Supporting visualizations and key findings
6. Your top three recommendations based on your analysis


## Business Task

Determine how casual riders and annual members use Cyclistic bikes differently in order to develop marketing strategies for converting casuals to members.

## Data Sources

I used csv files that contain trip data for the previous 12 months(December 2023 to November 2024), which can be found [here](https://divvy-tripdata.s3.amazonaws.com/index.html). Information within the files is as follows: <br /> <br />
RIDE_ID: a unique identifier for the trip <br />
RIDEABLE_TYPE: the type of vehicle <br />
STARTED_AT: the date and time that the trip started <br />
ENDED_AT: the date and time that the trip ended <br />
START_STATION_NAME: the station at which the trip began <br />
START_STATION_ID: the id of the station at which the trip began <br />
END_STATION_NAME: the station at which the trip ended <br />
END_STATION_ID: the id of the station at which the trip ended <br />
START_LAT: the latitude of the start station <br />
START_LNG: the longitude of the start station <br />
END_LAT: the latitude of the end station <br />
END_LNG: the longitude of the end station <br />
MEMBER_CASUAL: single-ride or full-day pass are casual riders. annual memberships are members

## Data Processing

After downloading the 12 files of interest, I imported them into an Oracle SQL database and combined them into a single "trips" table using the SQL Developer IDE's graphical user interface. Then, I proceeded to explore the data, where I found missing values, format discrepancies,
duplicate trips, and trips less than 1 minute in length.

Trips missing start or end stations were removed.

```
SELECT * FROM trips_original;
```
![alt text](/null_stations.png)
```
DELETE FROM trips
WHERE (start_station_name IS NULL AND start_station_id IS NULL) 
OR (end_station_name IS NULL AND end_station_id IS NULL);
```

Trips from June 2024 to November 2024 include milliseconds in their start and end times, but trips from December 2023 to May 2024 do not. The milliseconds were removed from the timestamps so that the format of the data would be consistent.

```
```

Duplicate trips were found as a result of the same trip being in multiple csv files. This is because there are trips that start on the last day of one month and end on the first day of the next. As a result, a trip like that would end up in two different month's files. Duplicates were removed. 

```
```

Trips less than one minute were removed (potentially false starts or users trying to re-dock a bike to ensure it was secure). 

```
```

Code was run to remove any leading and trailing whitespace from various column's values just in case any unwanted whitespace was present

```
```



