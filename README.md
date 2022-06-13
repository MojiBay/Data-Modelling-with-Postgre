

### Discuss the purpose of this database in the context of the startup, Sparkify, and their analytical goals.

A startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. The analytics team is particularly interested in understanding what songs users are listening to. Currently, they don't have an easy way to query their data. Thus, they asked me to create a Postgres database with tables designed to optimize queries on song play analysis. 

Their data set looks like this:
- a directory of JSON logs on user activity on the app.
- a directory with JSON metadata on the songs in their app.

My pathway:

I. Create a postgres database schema.
II. Create an ETL pipeline using python and SQL that transfers data from files in the aforementioned directories into fact and dimension tables explained below.


### State and justify your database schema design and ETL pipeline.

Schema for Song Play Analysis

 Using the song and log datasets, I created a star schema. with:

one fact table: containing all the measures associated with each event songplays.
 4-dimensional tables: songs, artists, users and time, each with a primary key that is being referenced from the fact table.

 The schema tables in detail:

Fact Table

songplays - records in log data associated with song plays i.e. records with page NextSong
songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent

Dimension Tables
users - users in the app
user_id, first_name, last_name, gender, level
songs - songs in music database
song_id, title, artist_id, year, duration
artists - artists in music database
artist_id, name, location, latitude, longitude
time - timestamps of records in songplays broken down into specific units
start_time, hour, day, week, month, year, weekday




### An explanation of the files in the repository.

The project workspace includes:

1. data folder: containing two folders 'log_data' and 'song_data' in which all needed jsons reside.

2. test.ipynb displays the first few rows of each table to let you check your database.

> %sql SELECT * FROM time LIMIT 5;


3. create_tables.py drops and creates your tables. You run this file to reset your tables before each time you run your ETL scripts.

4. etl.ipynb reads and processes a single file from song_data and log_data and loads the data into your tables. This notebook contains detailed instructions on the ETL process for each of the tables.

5. etl.py reads and processes files from song_data and log_data and loads them into your tables. You can fill this out based on your work in the ETL notebook.

6. sql_queries.py contains all your sql queries, and is imported into the last three files above.

7. README.md provides discussion on your project.

8. runpage.ipynb where you can run the .py files.


### Order of action

1. run sql_queries.py
2. run create_tables.py
3. run test.ipynb. Restart the kernel after running.
4. run etl.ipynb
5. run etl.py





### How to run the Python scripts.

1. Go to runpage.ipynb
2. %run sql_queries.py : Executes sql_queries
3. %run create_tables.py : Executes create_tables
4. %run etl.py : Runs etl.py





