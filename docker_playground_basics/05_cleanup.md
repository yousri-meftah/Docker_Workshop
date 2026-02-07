# 05 - Cleanup

If you want to remove everything created in the playground:

## Stop and remove any leftover containers
```bash
docker ps -a
```
```bash
docker rm -f alpine-demo web
```

## Remove the volume (if still present)
```bash
docker volume rm demo-data
```

## Remove the network (if still present)
```bash
docker network rm demo-net
```

## Remove the images (optional)
```bash
docker rmi alpine:latest nginx:alpine
```
