# Introduction

# Getting Started
## Start the infrastructure
```
docker-compose up -d
```

## Load the kafka topics
Assuming you _don't_ have the Kafka tools installed locally
```
docker-compose exec schema-registry /scripts/populate_topics --docker --all 
```


## Load the kafka topics - outside container
If you  _do_ have the Kafka tools installed locally (eg., `kafka-avro-console-producer`)
```
./scripts/populate_topics --all
```





## KSQL
```
docker-compose exec ksql-cli ksql http://ksql-server:8088
```

[Most of the KSQL stuff](./scripts/demo.ksql)


## Advanced Automated Example
Using the super useful [mockaroo](http://mockaroo.com) service we can generate some randomized data simulating insurance events.  
```
curl --silent "https://api.mockaroo.com/api/772da520?count=5&key=ef63f310"
```

Gives responses like this
```
{"customer_name":"Gwenette","phone_model":"iPhone 6s","event":"submerged in water","post_code":2830}
{"customer_name":"Barret","phone_model":"Oppo","event":"submerged in water","post_code":4009}
{"customer_name":"Tommy","phone_model":"Alcatel X1","event":"stolen by kangaroo","post_code":2830}
{"customer_name":"Pennie","phone_model":"Onplus 3T","event":"vaporized by canon","post_code":2830}
{"customer_name":"Martin","phone_model":"Oppo","event":"crushed by tree","post_code":2830}
```

If we want to genrate an insurance event every second, run the following
```
watch --interval 1 'curl --silent "https://api.mockaroo.com/api/772da520?count=1&key=ef63f310" | ./populate_topics --load_phone_event_int'
```

