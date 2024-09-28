# Kafka Compose

A sample docker-compose to start a Kafka cluster with 3 brokers

Reference: https://github.com/confluentinc/cp-all-in-one/tree/7.5.0-post/cp-all-in-one-community

## Start

```
docker-compose up -d
```

Note: by default this setup uses both `docker-compose.yml`, which contains primary setup for the Kafka cluster and `docker-compose.conduktor.yml` which contains a web UI (https://docs.conduktor.io/platform/) for Kafka

If you don't want to use Lenses UI, edit `COMPOSE_FILE` variable in `.env` to exclude `docker-compose.conduktor.yml` before running `docker-compose up`

Conduktor web UI is accessible at http://localhost:8080 with username `admin@local.com`, password `admin`

## Common operations

- Topic
    - Create: `task topic:create -- {topic-name}`
    - List: `task topic:list`
    - Describe: `task topic:describe -- {topic-name}`

- Console producer/consumer
    - Start console producer: `task console:producer -- {topic-name}`
    - Start console consumer: `task console:consumer -- {topic-name}`

- Consumer group
    - List: `task group:list`
    - Describe: `task group:describe -- {group-name}`
    - Delete: `task group:delete -- {group-name}`
    - Reset offsets: `task group:reset-offsets -- {group-name}`
