# Kafka

## Usage

- Messaging 
  - traditionnal message broker
  - similar to RabbitMQ or ActiveMQ
  - (+) better throughput, built-in partitioning, replication, and fault-tolerance 
  
- Website Activity Trackin
  - to rebuild a user activity tracking pipeline as a set of real-time publish-subscribe feeds
  - site activity (page views, searches, or other actions users may take) is published to central topics with one topic per activity type
  
- Metrics
  - operational monitoring data
  
- Log Aggregation
  - replacement for a log aggregation solution
  - allows for lower-latency processing and easier support for multiple data sources and distributed data consumption
  - (+) in comparison to log-centric systems like Scribe or Flume, Kafka offers equally good performance, stronger durability guarantees due to replication, and much lower end-to-end latency.
  
- Stream Processing
  - Many users of Kafka process data in processing pipelines consisting of multiple stages, where raw input data is consumed from Kafka topics and then aggregated, enriched, or otherwise transformed into new topics for further consumption or follow-up processing
  
- Event Sourcing
  - Event sourcing is a style of application design where state changes are logged as a time-ordered sequence of records
  - (+) Kafka's support for very large stored log data makes it an excellent backend for an application built in this style. 
  
- Commit Log
  -Kafka can serve as a kind of external commit-log for a distributed system. The log helps replicate data between nodes and acts as a re-syncing mechanism for failed nodes to restore their data

- [other use case] https://engineering.linkedin.com/distributed-systems/log-what-every-software-engineer-should-know-about-real-time-datas-unifying

replication, fault tolerance

