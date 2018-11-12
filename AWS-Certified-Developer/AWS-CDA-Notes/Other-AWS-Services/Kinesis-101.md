# Kinesis 101
## What is streaming data?
Streaming data is data that is generated continuously by thousands of data sources, which typically send in the data records simultaneously, and in small sizes (order of Kilobytes)

- Purchase from online stores (think amazon.com)
- Stock Prices
- Game data (as the gamer plays)
- Social network data (every time you update status, or post to friends wall)
- Geospatial data (think uber.com)
-IoT sensor data (sensors arround the world monitoring temperatures)

## What is Kinesis?
Amazon Kinesis is a platform on AWS to send your streaming data too. Kinesis makes it easy to load and analyze streaming data, and also providing the ability for you to build your own custom applications for your business needs

## What are the core Kinesis Services
- Kinesis Streams
- Kinesis Firehose
- Kinesis Analytics


## Kinesis Streams

![Image](https://i.imgur.com/Zav7y77.jpg)

- Kinesis Streams consists of shards
    - 5 transactions per second for reads, up to a maximum total data read rate of 2 MB per second and up to 1,000 records per second for writes, up to a maximum total data write rate of 1 MB per second (including partition keys)
    - The data capacity of your stream is a function of the number of shards that you specify for the stream. The total capacity of the stream is the sum of the capacities of its shards

## Kinesis Firehose
![Image](https://i.imgur.com/hgd9AkY.jpg)

![Image](https://i.imgur.com/m6e3f2P.jpg)

![Image](https://i.imgur.com/qySOrpL.jpg)

- You don't need to worry about data consumers
- Don't have to worry about the management of shards

## Kinesis Analytics 
![Image](https://i.imgur.com/q1n0285.jpg)

## Kenesis - Exam Tips
- know the difference between Kinesis Streams and Kinesis Firehose. You'll be given scenario questions and you must choose the most relevant services
- Remember the core architecture differences
- If you see a question talking about shards, you'll know its **Kinesis Streams**
- If it's talking about analyzing data, automaticaly using Lambda, and not having to worry about data consumers, thats going to be **Kinesis Forehose**

