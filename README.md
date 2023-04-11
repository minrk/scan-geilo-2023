# sample image for mpi + ipyparallel + dolfinx + jupyter-book

Use the image:

```bash
docker pull ghcr.io/minrk/scan-geilo-mpi-2023
docker run --rm -it -v $PWD:/home/mambauser/mnt -p 127.0.0.1:8888:8888 ghcr.io/minrk/scan-geilo-mpi-2023
```

Build the image with:

```
docker buildx build -t ghcr.io/minrk/scan-geilo-mpi-2023 --platform linux/arm64 --platform linux/amd64 image --push
```
