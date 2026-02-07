# 03 - Volumes

Goal: see why data disappears without volumes, then fix it.

We will first create a file inside a container, then start a new container and show the file is gone. After that, we will use a named volume to persist data.

## The problem: data disappears without a volume
```bash
docker run --rm -it alpine:latest sh
```

Inside the container:
```sh
mkdir -p /data
echo "temp data" > /data/hello.txt
ls -l /data
exit
```

Start a new container:
```bash
docker run --rm -it alpine:latest sh
```

Inside the container:
```sh
ls -l /data
cat /data/hello.txt
exit
```

Expected: `/data` does not exist or `hello.txt` is missing.

## Create a named volume
```bash
docker volume create demo-data
```

## List volumes
```bash
docker volume ls
```

## Use the volume in a container
```bash
docker run --rm -it \
  -v demo-data:/data \
  alpine:latest sh
```

Inside the container:
```sh
echo "hello volume" > /data/hello.txt
ls -l /data
cat /data/hello.txt
exit
```

## Verify the data persists (new container)
```bash
docker run --rm -it \
  -v demo-data:/data \
  alpine:latest sh
```

Inside the container:
```sh
cat /data/hello.txt
exit
```

## Remove the volume (optional)
```bash
docker volume rm demo-data
```
