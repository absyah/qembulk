# Build and Run the Qembulk image
## To build Docker image

``` bash
$ cd /path/to/root/dir/of/qembulk
$ docker build -t qembulk:latest -f dockerfile/Dockerfile .
```

## To run Docker container

```bash
$ docker run -itd -v `pwd`:/root/app --name qembulk qembulk:latest /bin/bash
```

## Accessing the container

Login to running container via `docker exec` command.

```bash
$ docker exec -it {CONTAINER ID} /bin/bash
```

## Run bundle

```bash
cd ~/app/embulk_bundle
embulk bundle
```

## Run embulk

```bash
cd ~/app
embulk run -b ./embulk_bundle/ config.yml
```
