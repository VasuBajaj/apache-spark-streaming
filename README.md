# Instructions

## Basic Concept - Visual
![](https://spark.apache.org/docs/latest/img/structured-streaming-stream-as-a-table.png)

A query on the input will generate the “Result Table”. Every trigger interval (say, every 1 second), new rows get appended to the Input Table, which eventually updates the Result Table. Whenever the result table gets updated, we would want to write the changed result rows to an external sink.

![](https://spark.apache.org/docs/latest/img/structured-streaming-model.png)

### Example

![](https://spark.apache.org/docs/latest/img/structured-streaming-example-model.png)


Official Guide - https://spark.apache.org/docs/latest/structured-streaming-programming-guide.html 




## Interview Questions 

- How is Spark Structured Streaming different from Kafka Streams?

Kafka analyses the events as they unfold. As a result, it employs a continuous (event-at-a-time) processing model. Spark, on the other hand, uses a micro-batch processing approach, which divides incoming streams into small batches for processing.

- Why is Structured Streaming being preferred over DStreams?

Structured Streaming offers exactly-once delivery with 100+ milliseconds latency, whereas the Streaming with DStreams approach only guarantees at-least-once delivery, but can provide millisecond latencies.
DStream is just a collection of RDDs, it’s typically used for low-level transformations and processing. Adding a DataFrames API on top of that provides very powerful abstractions like SQL, but requires a bit more configuration.
 
- Are there any use-cases where one should prefer DStreams over Structured Streaming?

Structured Streaming is more inclined to real-time streaming but Spark Streaming focuses more on batch processing. The APIs are better and optimized in Structured Streaming where Spark Streaming is still based on the old RDDs.

- How is Spark Structured Streaming different from Apache Flink?

Flink is based on the operator-based computational model where as Apache Spark is based on the micro-batch model.

reference -  https://data-flair.training/blogs/comparison-apache-flink-vs-apache-spark/ 

- What is a Tumbling window?

![](https://spark.apache.org/docs/latest/img/structured-streaming-time-window-types.jpg)

Tumbling windows are a series of fixed-sized, non-overlapping and contiguous time intervals. An input can only be bound to a single window.

Sliding windows are similar to the tumbling windows from the point of being “fixed-sized”, but windows can overlap if the duration of slide is smaller than the duration of window, and in this case an input can be bound to the multiple windows.


- What have supported data sources in Spark Streaming?

Spark Streaming provides out of the box connectivity for various source systems. It provides built in support for Kafka, Flume, Twitter, ZeroMQ, Kinesis and Raw TCP

- How does fault tolerance is ensured in Spark Streaming?

If the driver node fails, all the data that was received and replicated in memory will be lost. This will affect the result of the stateful transformation. To avoid the loss of data, Spark 1.2 introduced write ahead logs, which save received data to fault-tolerant storage. All the data received is written to write ahead logs before it can be processed to Spark Streaming.
Write ahead logs are used in database and file system. It ensure the durability of any data operations. It works in the way that first the intention of the operation is written down in the durable log. After this, the operation is applied to the data. This is done because if the system fails in the middle of applying the operation, the lost data can be recovered. It is done by reading the log and reapplying the data it has intended to do.

| Deployment Scenario |	Worker Failure |	Driver Failure |
|--|--|--|
|Spark 1.1 or earlier	| Buffered data lost with unreliable receivers	| Buffered data lost with the unreliable receiver|
|Spark 1.2 or later | without write ahead logs	Zero data loss with reliable receivers, At-least-once semantics	| Past data lost with all receivers, Undefined semantics
|Spark 1.2 or later | with write ahead logs	Zero data loss with reliable receivers, At-least-once semantics	| Zero data loss with reliable receivers and files, At-least-once semantics |


- What are some of the limitations of Spark Structured Streaming API?

Users must write programming code and understand complex Apache Spark concepts to set up an optimal performing ETL pipeline.
The number of offered connectors are minimal.  Consequently, users must develop and maintain their connector and sink source code.

- What types of joins are supported in Spark Structured Streaming API?

- Join Operations
- Stream-static Joins
- Stream-stream Joins
- Inner Joins with optional Watermarking
- Outer Joins with Watermarking
- Semi Joins with Watermarking
- Support matrix for joins in streaming queries

reference - https://spark.apache.org/docs/latest/structured-streaming-programming-guide.html#join-operations

- Can we integrate machine learning with Spark Structured Streaming?

yes - example reference - https://towardsdatascience.com/learn-how-to-use-spark-ml-and-spark-streaming-3a731485d052


