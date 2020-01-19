# Kafka Compose

A sample docker-compose to start a Kafka cluster with 3 brokers

Reference: https://github.com/confluentinc/examples/tree/5.4.0-post/cp-all-in-one-community

## Start

```
docker-compose up -d
```

Note: by default this setup uses both `docker-compose.yml`, which contains primary setup for the Kafka cluster and `docker-compose.lenses.yml` which contains a web UI (https://github.com/lensesio/kafka-topics-ui) for Kafka

If you don't want to use Lenses UI, edit `COMPOSE_FILE` variable in `.env` to exclude `docker-compose.lenses.yml` before running `docker-compose up`

Lenses web UI is accessible at http://localhost:8000

## Common operations

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
