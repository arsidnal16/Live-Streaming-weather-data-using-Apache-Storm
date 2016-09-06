# Weather-Event-Streamer
Real Time Weather Event Analysis Processing Streamer

This project is implemented to stream and analyze real time weather
data using Apache Kafka and Apache Storm in hortonworks
sandbox available in Azure cloud environment.

Need horton sandbox account, preferably in a cloud environment like AWS or Azure

Please replace the API key variable with the API key you got when you registered with Forecast.io API. 

The Forecast.io API has a limit of 1000 calls per day so I have selected the weather data for 20 biggest cities in the world and used Apache Kafka to produce weather events. 

These events are then consumed using Apache Storm and then stored in HBase using hive.

The Hortonworks Sandbox HDP 2.4 is available on Micosoft Azure. The Historical data for weather is the data collected from NCDC. This is the Global Surface Summary of day(GSOD) data. This data can be found here ftp://ftp.ncdc.noaa.gov/pub/data/gsod/


Commands to run:

java -cp target/Weather-Event-Streamer-0.0.1-SNAPSHOT.jar producer/WeatherEventsProducer sandbox.hortonworks.com:6667 sandbox.hortonworks.com:2181

storm jar target/Weather-Event-Streamer-0.0.1-SNAPSHOT.jar consumers.WeatherEventProcessingTopology
