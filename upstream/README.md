build

```shell
docker build -t envoy_discovery_upstream .
docker tag envoy_discovery_upstream guitarrapc/envoy_discovery_upstream:latest
docker push guitarrapc/envoy_discovery_upstream:latest
```

start

```shell
docker run -it -p 8081:8081 guitarrapc/envoy_discovery_upstream:latest
```
