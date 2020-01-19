# Kafka Compose

A sample docker-compose to start a Kafka cluster with 3 brokers

Reference: https://github.com/confluentinc/examples/tree/5.4.0-post/cp-all-in-one-community

### Create a topic

```
docker-compose broker-1 kafka-topics \
	--bootstrap-server broker-1:19092 \
	--create \
	--partitions 3 \
	--replication-factor 2 \
	--topic test-topic
```

### List topics

```
docker-compose broker-1 kafka-topics \
	--bootstrap-server broker-1:19092 \
	--list
```

### Describe a topic

```
docker-compose broker-1 kafka-topics \
	--bootstrap-server broker-1:19092 \
	--topic test-topic \
	--describe
```

### Publish a message using console producer

```
docker-compose broker-1 kafka-console-producer \
  --broker-list broker-1:19092,broker-2:29092,broker-3:39092 \
  --topic test-topic
```

### Consume messages using console consumer

```
docker-compose broker-1 kafka-console-consumer \
  --bootstrap-server broker-1:19092,broker-2:29092,broker-3:39092 \
  --topic test-topic --from-beginning
```
