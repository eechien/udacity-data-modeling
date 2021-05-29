# Sparkify

Sparkify is a music streaming app that's interested in what songs users are listening to.
For example, they may want to create playlists of the top hits in the USA. In order to 
more easily query their data, they need to move their JSON song and log files into a database.
This project moves that data into a PostgreSQL database via an ETL pipeline.

## Database schema

This schema uses the star schema format where songplays is the fact table and artists, songs,
users, and time are the dimension tables because Sparkify is most interested in what songs are
actually getting played. This allows us to more easily aggregate the data around song plays.

![Sparkify database schema diagram](schema_diagram.png)

The `songs` and `artists` tables are populated by the song_data files. While `time`, `users`,
and `songplays` comes from our log_data files.

## Files in repo

- data
  - log_data
    - Contains JSON data on user activity.
  - song_data
    - Contains JSON data of songs.
- create_tables.py
  - Drops tables if they exist, then recreates the tables.
- etl.py
  - ETL pipeline for extracting data from log_data and song_data into the tables created by create_tables.py
- sql_queries.py
  - Contains the SQL queries for creating, inserting, and dropping tables
- etl.ipynb
- test.ipynb

## Running the project

First create the tables by running:
`python create_tables.py`

Next execute the ETL pipeline by running:
`python etl.py`