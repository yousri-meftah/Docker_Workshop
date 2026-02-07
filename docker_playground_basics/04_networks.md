# 04 - Networks

Goal: see how containers talk to each other on a user-defined network.

We will create a bridge network and run two containers.

## Create a network
```bash
docker network create demo-net
```

## Run a web container on the network
```bash
docker run -dit \
  --name web \
  --network demo-net \
  nginx:alpine
```

## Run a client container on the same network
```bash
docker run -it --rm \
  --name client \
  --network demo-net \
  alpine:latest sh
```

Inside the client container:
```sh
apk add --no-cache curl
curl -I http://web
exit
```

Expected: HTTP response headers from nginx.

## List networks
```bash
docker network ls
```

## Inspect the network
```bash
docker network inspect demo-net
```

## Cleanup this section
```bash
docker rm -f web
```
```bash
docker network rm demo-net
```
