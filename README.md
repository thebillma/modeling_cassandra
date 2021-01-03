# Data Modeling with Cassandra

## Project Description

A compagny that has been collecting songs' data and users activity wants an efficient model to store and analyze the data. The data currently resides in folders in CSV format.
This project consists of creating a database and build an ETL pipeline to store the data.
This will help the analytics to analyze and derive insights from data.

## Data description
The dataset is a set of CSV files in folders partitioned by date. Here is an example:

 - **event_data/2018-11-08-events.csv**
 - **event_data/2018-11-09-events.csv**

The project consist of extracting data from the CSV and load in a cassandra table to answers the questions below:

1- Give me the artist, song title and songs's length in the music app history that was heard during sessionId = 338 and itemInsession = 4
