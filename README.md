# Introduction

# Getting Started
## Start the infrastructure
```
docker-compose up -d
```

## Load the kafka topics
Assuming you _don't_ have the Kafka tools installed locally
```
docker-compose exec schema-registry /scripts/populate_topics --docker
```


## Load the kafka topics - outside container
If you  _do_ have the Kafka tools installed locally (eg., `kafka-avro-console-producer`)
```
./scripts/populate_topics
```





## KSQL
```
docker-compose exec ksql-cli ksql http://ksql-server:8088
```

[Most of the KSQL stuff](./scripts/demo.ksql)



