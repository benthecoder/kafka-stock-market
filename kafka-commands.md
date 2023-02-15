# installation

## install kafka

head to <https://downloads.apache.org/kafka/> and download the latest version of kafka

```bash
wget https://downloads.apache.org/kafka/3.3.2/kafka_2.13-3.3.2.tgz
tar -xvf kafka_2.13-3.3.2.tgz
```

```bash
java -version
sudo yum install java-1.8.0-openjdk
java -version
cd kafka_2.13-3.3.2
```

## Start Zoo-keeper

```bash
bin/zookeeper-server-start.sh config/zookeeper.properties
```

## Start Kafka-server

It is pointing to private server:

- do `sudo vi config/server.properties`
- change advertised_listeners to public ip of the EC2 instance

```bash
# increase kafka memory
export KAFKA_HEAP_OPTS="-Xmx256M -Xms128M"
cd kafka_2.13-3.3.2
bin/kafka-server-start.sh config/server.properties
```

## Create the topic

```bash
cd kafka_2.13-3.3.2
bin/kafka-topics.sh --create --topic demo_test --bootstrap-server <MY_PUBLIC_IP>:9092 --replication-factor 1 --partitions 1
```

## Start Producer

```bash
cd kafka_2.13-3.3.2
bin/kafka-console-producer.sh --topic demo_test --bootstrap-server <MY_PUBLIC_IP>:9092
```

## Start Consumer

```bash
cd kafka_2.13-3.3.2
bin/kafka-console-consumer.sh --topic demo_test --bootstrap-server <MY_PUBLIC_IP>:9092
```

Following this, you should have 4 panes of terminal open, one for zookeeper, one for kafka, one for producer and one for consumer.
