# Instructions






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
- What have supported data sources in Spark Streaming?
- How does fault tolerance is ensured in Spark Streaming?
- What are some of the limitations of Spark Structured Streaming API?
- What types of joins are supported in Spark Structured Streaming API?
- Can we integrate machine learning with Spark Structured Streaming?
