# Repository name: Docker - Mongo replicaset

# Description
- This repo implement `Dockerfile` to build `mongo replicaset image` on docker.
- You can find the docker image run for `arm64` device at https://hub.docker.com/r/vosylienthanh/mongo-local-replicaset-arm64
- For other devices, you can build image by yourself

# How to use
## Build command

### Build for arm64 arch
```BASH
docker build -t vosylienthanh/mongo-local-replicaset-arm64:0.0.1 -t vosylienthanh/mongo-local-replicaset-arm64:lastest .
```

### Build for x64_86 arch
```BASH
docker build -t vosylienthanh/mongo-local-replicaset-intel:0.0.1 -t vosylienthanh/mongo-local-replicaset-intel:lastest .
```

## Push to docker hub command

### Push mongo-local-replicaset-arm64
```BASH
docker push vosylienthanh/mongo-local-replicaset-arm64:0.0.1
docker push vosylienthanh/mongo-local-replicaset-arm64:lastest
```

### Push mongo-local-replicaset-intel
```BASH
docker push vosylienthanh/mongo-local-replicaset-intel:0.0.1
docker push vosylienthanh/mongo-local-replicaset-intel:lastest
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
