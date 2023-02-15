# Notes

- [Notes](#notes)
  - [What is Kafka?](#what-is-kafka)
    - [capabilities](#capabilities)
    - [applications of stream processing](#applications-of-stream-processing)
    - [concepts](#concepts)
    - [Kafka APIs](#kafka-apis)
  - [Zookeper](#zookeper)
  - [Topics](#topics)
  - [Glossary](#glossary)

## What is Kafka?

[Apache Kafka](https://kafka.apache.org/) is a distributed event store and stream processing platform.

where

- distributed event store: a distributed network for storing events (clicks, purchases, user signups, etc.)
- stream processing: performing continuous computation on a potentially unbounded stream of events (like a river)

### capabilities

1. enables applications to publish or subscribe to data or event streams
2. stores records accurately (sequential order) in a fault-tolerant way
3. processes records in real-time

### applications of stream processing

- fintech: real-time stock market analysis
- e-commerce: real-time product recommendations
- banks: real-time fraud detection

### concepts

basic idea

- producer -(write)-> broker/cluster -(read)-> consumer

where

- producers: pulls messages from topics and writes to broker
- broker: receives and store messages, multiple single node (i.e. ec2 machine) forms a cluster
- consumer: reads data from broker
- each of them can be n clusters to be distributed

### Kafka APIs

- Producer API: allows apps to make streams of data, creates records and produces to topics (an ordered list of events that persists temporarily depending on storage)
- Consumer API: subscribes to one or more topics and listens and ingests data
- Streams API: Producer -> transform data (Streams) -> Consumer. In a simple application, Producer -> Consumer is enough where data doesn't change.
- Connector API: Reusable producer and consumer (package code for other developers to reuse and integrate for their purposes)

## Zookeper

Zookeeper (for kafka) makes sure all servers are running properly. if one broker dies, it notifies the other. It also does security management.

- Open Source Apache Project
- Distributed Key Value Store
- Maintains configuration information
- Stores ACLs and Secrets
- Enables highly reliable distributed coordination
- Provides distributed synchronization

## Topics

Stream of "related" messages in Kafka

- topics allows consumer to specify what they want to consume from the producer
- like a label for a stream of data
- can be unlimited

within topics you can have n partitions and each partition is an ordered, immutable sequence of records that is continually appended to a log

## Glossary

- stream : unbounded sequence of ordered, immutable data
- stream processing: continual calculations performned on one or more streams
- immutable data: data that cannot be changed
- event: immutable fact about something that has happened in the past
- broker: a single member server of kafka cluster
- cluster: a group of one or more kafka brokers working together to satisfy kafka production and consumption
- Node: a single computing instance (physical server in datacenter or virtual machine in cloud)
- zookeper: used by kafka brokers to determine which broker is the leader of a given partition and topic, and track cluster membership and configuration for kafka
- data partition: kaflka topics consist of one or more partitions. partition is a log which provides ordering guarantees for all data contained, they are chosen by hashing key values.
