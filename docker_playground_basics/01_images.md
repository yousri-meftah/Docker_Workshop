# 01 - Images

Goal: understand what an image is and how to work with it.

We will use a lightweight image: `alpine`.

## Pull an image
```bash
docker pull alpine:latest
```

## List local images
```bash
docker images
```

## Inspect the image
```bash
docker image inspect alpine:latest
```

## Remove the image (optional)
```bash
docker rmi alpine:latest
```

If you removed it, pull again before the next step.
