# Data Modeling Project


### The following project describes the creation a Sparkify, a music streaming app that contains songs and user activity, and will help the company understand what songs the users are listening in order to analyze and take decisions  about what songs can be recommended for each user as a client.

The files worked on these project are the following:

1. sql_queries.py -> contains the DROP, CREATE, INSERT statements lists for each table of the database model. It also contains a query to get the id of songs and artist used for loading data in some of the steps.

2. create_tables.py ->  makes the connection to the sparkify database and runs the queries lists from sql_queries to create the tables of the model.

3. etl.ipynb -> develops the ETL process - process the 2 sources: 
    a) Songs_data to insert data to songs and artists tables.
    b) Log_data to insert data to time, users and songplays table.

4. etl.py -> runs the proccess previously created on the etl.ipynb to insert the complete datasets into the tables. *.py files should be run on the terminal.

5. test.ipynb -> this file is used accross each step to test that the code is working correctly: tables are created, tables have data and shows it correctly.


**To run each python script, you should go to the terminal. Example: python create_tables.py and then click enter.**

### About the data modeling:

1. This is a  star schema with a fact table (songplays) and 4 dimension tables (users, artists, songs and time). As mentioned above, DROP, CREATE, INSERT and SELECT statements are define in sql_queries.py. Create_tables.py uses the following functions to create the database sparkifydb and the tables: create_database, drop_tables, create_tables.
2. The type of the fields have been specified based on the values that come from the datasets. Primary keys have been established in the CREATE statements. A particular case is the songplay_id which is SERIAL type as this is defined as an auto-increment field because we don´t have this value from the sources.
3. The ETL process in etl.py load the data from JSON song files into the songs and artists tables. Using the JSON log files, time and users tables are populated. To populate the songplays table, a SELECT query is used to pull the song and artist id and combine with the other data to pull the neccesary rows.

#### Some queries to check relevant information:

- Get number of users in the model:
%sql SELECT COUNT(user_id) FROM users;

- Number of songs per year:
%sql SELECT year,count(*) FROM songs GROUP BY year ORDER BY 1;

- Number of artists
%sql SELECT COUNT(artist_id) FROM artists;

- Number of rows in songplays: 
%sql SELECT COUNT(*) FROM songplays;


