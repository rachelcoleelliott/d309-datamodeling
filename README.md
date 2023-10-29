# Data Modeling with Postgres

## _D309: Data Modeling_
---

Final Project from Udacity's Data Analytics Nanodegree Data Modeling course. This project uses the following resources:

- Python programming lanugaes
- SQL programming language
- Pandas Python library
- PostgreSQL database


## Introduction: Purpose and Context
---
A startup music streaming company would like to analyze data they've collected on songs and user activity on their new app. They do not yet have an efficient way to query data for analysis as all of the data is in JSON files. They would like a data engineer to create a database with tables designed for efficient analysis on song play. My goal in this project was to create a database schema and ETL pipeline for this analysis.



## Files and Folders
---
  - Data folder: contains JSON logs with data used for table creation
  -  etl.py: Python code for pipeline
  - test.ipynb: Testing environment for table data creation and inserts
  - create_tables.py: Python script for creating tables and inserting values. Queries created in sql queries file
  - sql_queries: SQL queries for creating tables and inserting values
 

## Database Schema Design
---
With the two datasets provided (the two JSON logs), I created five tables: song_plays, users, songs, artists, and time. With song_plays as the fact table, and the other four as dimension tables. Song_plays primary key was songplay_id, with foreign keys being start_time, user_id, song_id, and artist_id.


## Tables
---
##### Songs
For the songs table, I read the JSON files (TRAAAAW128F429D538.json), then created a dataframe with song_id, title, artist_id, year, and duration as the columns.

##### Artists
For the artists table, I used the same JSON file as the songs table and pulled the artist_id, artist_name, artist_location, artist_latitude, and artist_longitude.

##### Time
For the time table, I read the JSON file from the daily log data (2018-11-01-events.json). These files first had to be filtered by the item "NextSong" as the file contained disorganized data. NextSong marked the next datapoint or row for the table. The timestamp portion of this dataset needed to be converted to the datetime datatype (it was in milliseconds). After the conversion I could extract data. I needed to extract the timestamp, hour, day, week of year, month, year, and weekday. I created the column labels, then created a dictionary with the extracted timestamp data and labels, then converted it into a dataframe. After this, I could insert the values into the time table.

##### Users
In the users table, I read the JSON file from the daily log data. I used the userId, firstName, lastName, gender, and level for this table.

##### Song_plays (Fact table)
For the songplay table, it was a bit more complex. I had to use the SQL song_select query to get the information from the songs, artists, and originial log file. To get the song Id and artist Id, I found matches based on song title, artist name, and song duration time from the songs and artists table.
I used the timestamp, user_id, level. song_id, artist_id, session_id, location and user_agent to insert into the song_plays table.



### Attributions

---

| Website Name | Link |
| ------ | ------ |
| StackOverflow | [https://stackoverflow.com/] |
| W3Schools | [w3schools.com/python] |
| Github | [github.com] |
| Pandas.PyData | [https://pandas.pydata.org/] |
| GeeksforGeeks | [https://www.geeksforgeeks.org/pandas-tutorial/] |

