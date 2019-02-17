# Introduction

# Getting Started
## Start the infrastructure
```
docker-compose up -d
```

## Load the kafka topics
```
cat repair.json | ./read_repair
cat post_code.json | ./read_post_code
cat phone_event.json | ./read_phone_event
```


## KSQL
```
docker-compose exec ksql-cli ksql http://ksql-server:8088
```

[Most of the KSQL stuff](./demo.ksql)


