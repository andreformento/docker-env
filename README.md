# Docker-env image

Local build:
```shell
docker build -t andreformento/docker-env:1.0.3 .
```

Publish:
```shell
docker push andreformento/docker-env:1.0.3
```

## Docker with prometheus

```shell
docker build -t prometheus-cli ./prometheus
docker run --rm -it prometheus-cli
```

- running a command inside this container
  ```shell
  docker run -v $(pwd)/myscript.sh:/tmp/myscript.sh \
             --entrypoint /tmp/myscript.sh \
             prometheus-cli
  ```
