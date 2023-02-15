# Real Time Stock Market Analysis with kafka

![architecture](architecture.jpeg)

## Technology Used

- Programming Language - Python
  - [dpkp/kafka-python: Python client for Apache Kafka](https://github.com/dpkp/kafka-python)
  - [fsspec/s3fs: S3 Filesystem](https://github.com/fsspec/s3fs)
- Apache Kafka
- Amazon Web Service (AWS)
  - EC2 - host kafka server
  - S3 (Simple Storage Service) - store data
  - Glue Crawler - create schema for data in S3
  - Glue Catalog - store schema for data in S3
  - Athena - Query data in S3

## setup and installation

Using conda

Create Conda environment

```bash
  conda create --name env_name python=3.8
```

Activate the environment

```bash
  conda activate env_name
```

Install requirements

```bash
  pip install -r requirements.txt
```

To reproduce this project 👇

1. Login to AWS console
2. Create ec2 instance
   - edit inbounds rules to allow custom -> my ip
   - ssh into EC2 instance
   - View [kafla commands](kafka-commands.md) for installing and setting up Kafka.
3. configure aws account with `aws cli` and `aws configure`
   - download csv file with credentials
4. create s3 bucket
   - run kafka producer and consumer notebooks to simulate streaming
5. create crawler in AWS Glue
   - choose s3 data source
   - create role in IAM and provide AdministratorAccess
   - create new database
   - run crawler
6. athena
   - create new s3 bucket to store output queries

## further improvements

- use real-time API
- create python program to run and show subscribing and publishing in terminal like below
  - [A small Kafka producer and consumer example](https://gist.github.com/NickLarsenNZ/e479c33f37a30ae4273f76dc2eab2a3e)

## References

- [📈 Stock Market Real-Time Data Analysis Using Kafka | End-To-End Data Engineering Project - YouTube](https://www.youtube.com/watch?v=KerNf0NANMo)
- [darshilparmar/stock-market-kafka-data-engineering-project](https://github.com/darshilparmar/stock-market-kafka-data-engineering-project)
