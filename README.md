# Data Lake with Spark in EMR Cluster



## **Overview**
For this project, Data Lake in EMR Cluster with spark and an ETL pipeline using Python was applied. The startup Sparkify wants to analyze the data they are collecting about music and user activity in its new music streaming app. We are currently collecting data in S3 Bucket and the json format and the analytics team is particularly interested in understanding what songs users are listening to.



## **Datasets**

**Song** - sample record:
```
{"num_songs": 1, "artist_id": "AR8IEZO1187B99055E", "artist_latitude": null, "artist_longitude": null, "artist_location": "", "artist_name": "Marc Shaiman", "song_id": "SOINLJW12A8C13314C", "title": "City Slickers", "duration": 149.86404, "year": 2008}
```

**Log** - sample record:
```
{"artist": "Sydney Youngblood", "auth": "Logged In", "firstName": "Jacob", "gender": "M", "itemInSession": 53, "lastName": "Klein", "length": 238.07955, "level": "paid", "location": "Tampa-St. Petersburg-Clearwater, FL", "method": "PUT", "page": "NextSong", "registration": 1.540558e+12, "sessionId": 954, "song": "Ain't No Sunshine", "status": 200, "ts": 1543449657796, "userAgent": ""Mozilla/5.0 (Macintosh; Intel Mac OS X 10_9_4) AppleWebKit/537.78.2 (KHTML, like Gecko) Version/7.0.6 Safari/537.78.2"", "userId": "73"}
```



## **Schema**

### Fact Table 

**songplays** - songplays of table
```
songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent
```

### Dimension Tables

**users**  - users of table
```
user_id, first_name, last_name, gender, level
```

**songs**  - songs of table
```
song_id, title, artist_id, year, duration
```

**artists**  - artists of table
```
artist_id, name, location, latitude, longitude
```

**time**  - time of table
```
start_time, hour, day, week, month, year, weekday
```


## Discussion of purpose

We modeled the database using the **Star Schema** Model, now we use **Apache Spark** in **EMR Cluster** a cloud service provided by AWS that allows data analysts, developers and data engineer to easily process large amounts of data.

We developed an automated pipeline to transfer information from JSON files stored in the **Amazon S3** cloud to **EMR Cluster** using Python, after processing the data, we saved the tables in a repository on Amazon S3.


## Project Files

```dl.cfg``` -> File for put your config of environment AWS.

```etl.py``` -> The ETL to reads data from **S3**, processes that data using **Spark**, and writes them back to **S3**.

```README.MD``` -> Description about process for this ETL pipeline. 
