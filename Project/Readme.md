# Data Modeling with Cassandra

### Project Description  

A compagny that has been collecting songs' data and users activity wants an efficient model to store and analyze the data. The data currently resides in folders in CSV format. This project consists of creating a database and build an ETL pipeline to store the data. This will help the analytics to analyze and derive insights from data.

### Data description  

##### The dataset is a set of CSV files in folders partitioned by date. Here is an example:  

   - **event_data/2018-11-08-events.csv**
   - **event_data/2018-11-09-events.csv**  
   
   
##### The project consist of pulling data from the CSV and load in a cassandra table to answer the questions below:  

###### 1- Give me the artist, song title and songs's length in the music app history that  was heard during sessionId = 338 and itemInsession = 4  

###### 2- Give me only the following: name of artist, song(sorted by itemInSession) and  user (first and last name for userid =10, sessionid = 182  
   
###### 3- Give me every user name(first and last) in my music app history who listened to  the songs 'All Hands Againgst His Own'  



### Table Modeling  

Three tables have been created for three queries provided above:  

1. **Table Name: music_library_artists_on_session**

     column 1: artist  
     column 2: item_in_session  
     column 3: length  
     Column 4: sessionid  
     Column 5: song  
     PRIMARY KEY(sessionid, item_in_session, )  
     
   **The columns output by the query are:**  
   
     column 1: artist  
     column 2: song  
     column 3: length
     
2. **Table Name: music_library_song_by_user_on_session**  

     column 1: artist  
     column 2: song  
     column 3: first_name  
     column 4: last_name  
     column 5: userid  
     column 6: sessionid  
     column 7: item_in_session  
     PRIMARY KEY(userid, sessionid, item_in_session)  
     
   **The columns output by the query are:**  
     
     column 1: artist  
     column 2: song  
     column 3: first_name  
     column 4: last_name   
     

3. **Tablea Name: music_library_users_by_song**  

     column 1: first_name  
     column 2: last_name  
     column 3: song  
     column 4: userid PRIMARY KEY (song, userid)  
     
   **The columns output by the query are:**  
   
     column 1: first_name  
     column 2: last_name



### Queries to answer the questions:  

###### 1- SELECT * FROM artist_song WHERE sessionid = 338 and item_in_sessionid = 4  

###### 2- SELECT * FROM artist_song WHERE sessionid = 182 and userid = 10 ORDER BY item_in_sessionid  

###### 3- SELECT * FROM artist_song WHERE song='All Hands Against His Own'