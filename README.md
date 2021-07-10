# Data Modeling with Cassandra

## Project Motivation

This is the second project of the Udacity Data Engineering Nanodegree. The task motivation was described as follows:

A startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. The analysis team is particularly interested in understanding what songs users are listening to. Currently, there is no easy way to query the data to generate the results, since the data reside in a directory of CSV files on user activity on the app.

They'd like a data engineer to create an Apache Cassandra database which can create queries on song play data to answer the questions, and wish to bring you on the project. Your role is to create a database for this analysis. You'll be able to test your database by running queries given to you by the analytics team from Sparkify to create the results.

They would like to run the following three queries:

1. Give me the artist, song title and song's length in the music app history that was heard during  sessionId = 338, and itemInSession  = 4
2. Give me only the following: name of artist, song (sorted by itemInSession) and user (first and last name) for userid = 10, sessionid = 182
3. Give me every user name (first and last) in my music app history who listened to the song 'All Hands Against His Own'

## Installation

- Install a recent version of python anaconda distribution. Use python3.
- Additionally install the following 3rd party libraries: pandas and cassandra_driver
- Install docker and pull the latest cassandra container

```
docker pull cassandra
docker run --name apache-cassandra-sparkifydb -p 9042:9042 -d cassandra:latest
```

## ETL Pipeline

The data is extracted from the different csv files into a single `event_datafile_new.csv`. From there the different tables are created in the jupyter notebook `Project_1B_ Project_Template.ipynb`. For the queries above three tables are created for NoSQL apache cassandra. Those tables are named as follows:

- `table_by_session_id_by_item_in_session` with artist, song, length, *sessionId*, *itemInSession* for Query 1. 
- `table_by_user_id_by_session_id` with artist, song, firstName, lastName, *userId*, *sessionId*, *itemInSession* for Query 2
- `table_by_song` with *song*, firstName, lastName, *userId* for Query 3

We labeled the used primary keys in italic.