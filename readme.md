# Repository name: Docker - Mongo replicaset

# Description
- This repo implement `Dockerfile` to build `mongo replicaset image` on docker.
- You can find the docker image run for `arm64` device at https://hub.docker.com/repository/docker/vosylienthanh/mongo-local-replicaset-arm64
- For other devices, you can build image by yourself

# How to use
## Build command
```BASH
docker build -t vosylienthanh/mongo-local-replicaset-arm64:0.0.1 -t vosylienthanh/mongo-local-replicaset-arm64:lastest .
```

## Push to docker hub command
```BASH
docker push vosylienthanh/mongo-local-replicaset-arm64:0.0.1
docker push vosylienthanh/mongo-local-replicaset-arm64:lastest
```

## Dockercompose file sample
```YAML
version: '3'
services:
  mongodb:
    container_name: mongodb
    image: vosylienthanh/mongo-local-replicaset-arm64:0.0.1
    ports:
      - "27017:27017"
      - "27018:27018"
      - "27019:27019"
    volumes:
      - local-data:/data/mongodb/data
    environment:
      - REPLICA_SET_NAME="rs0"
    restart: "always"
volumes:
  local-data:
```