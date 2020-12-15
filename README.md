# Microservices Workshop Images - Project Intro

This project provides the images to be used with the [AWS-microservices-workshop-hugo project](https://github.com/Redislabs-Solution-Architects/AWS-microservices-workshop-hugo), which is the workshop documentation that will consume the images produced here.

This project was originally forked from [Tug Grall's Microservices Demo](https://github.com/redis-developer/redis-microservices-demo) and the intention is to continue to track that project closely.

This project produces Docker images that can be run using docker, AWS Elastic Container Service (ECS) or Kubernetes.

At this time (2020-12-15) this project has focused on the AWS ECS approach, and hasn't actually tested out Kubernetes on AWS. 

# Original Intro to Microservices Demo

This project shows how you can modernize a legacy application that use RDBMS with Redis.

* Caching: Call Web Service and cache the result in Redis
* CDC to RediStreams: Capture MySQL transactionsd and send them to Redis Streams
* Use RediSearch to index relational data and provides autocomplete feature
* Store and Index data in Redis: copy the events from Streams and put them in a Redis Hash (Movie/Actors), this could be used as a cache or maine datastore 
* See how to run queries on Redis hashes using RediSearch commands (filter, sort, aggregate, and tull text search)
* Extend MySQL Legacy model with movie comments store in Hash and queried using RediSearch commands
* Push relationnoal data into RedisGraph
* a Web frontend developped with Vue.js

![Archi](./ui-redis-front-end/redis-front/public/imgs/overal-archi.png)

If you want to use the Web Service cache demo that call the OMDB API you must:

1. Generate a key here: [http://www.omdbapi.com/](http://www.omdbapi.com/) (do not forge to activate it, you will receive an email to which you must respond!)

2. When the application is ready go to the "Services" page and enter the key in the configuration screen, this will save the key in a Redis Hash (lool at `ms:config` during the demo)

## Running with Docker

### Run locally, no build

```
docker-compose up -d
```
### Run locally, with build

```
mvn clean package &&
docker-compose up --build -d
```

### Cleanup

```
docker-compose down -v --rmi local --remove-orphans

```

## Running/Building with ECS
See the [ECS instructions](./ECS-README.md)

## Deploy to Kubernetes

You can also deploy the application to Kubernetes, see [Kubernetes Readme](./kubernetes/README.md)
