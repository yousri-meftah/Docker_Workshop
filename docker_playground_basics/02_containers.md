# 02 - Containers

Goal: run a container, list it, and interact with it.

We will run an `alpine` container that prints a message then exits.

## Run a one-off container
```bash
docker run --rm alpine:latest echo "hello from a container"
```

## Start an interactive container
```bash
docker run -it --name alpine-demo alpine:latest sh
```

Inside the container, try:
```sh
uname -a
cat /etc/os-release
```

Exit the container:
```sh
exit
```

## List containers
```bash
docker ps      # running
```
```bash
docker ps -a   # all (including stopped)
```

## Start and stop a container
```bash
docker start alpine-demo
```
```bash
docker stop alpine-demo
```

## Execute a command in a running container
```bash
docker start alpine-demo
```
```bash
docker exec -it alpine-demo sh
```
```sh
echo "inside exec"
exit
```

## Remove the container
```bash
docker rm alpine-demo
```
