build

```shell
docker build -t envoy_discovery_sds .
docker tag envoy_discovery_sds guitarrapc/envoy_discovery_sds:latest
docker push guitarrapc/envoy_discovery_sds:latest
```

start envoy client.

```shell
./envoy -c envoy_config.yaml -l debug
```

start xds-server

```shell
docker run -it -p 8080:8080 guitarrapc/envoy_discovery_sds:latest
```

register upstream

```shell
curl -X POST --header 'Content-Type: application/json' --header 'Accept: application/json' -d '{
  "hosts": [
    {
      "ip_address": "127.0.0.1",
      "port": 8081,
      "tags": {
        "az": "us-central1-a",
        "canary": false,
        "load_balancing_weight": 50
      }
    }
  ]
}' http://localhost:8080/edsservice/myservice
```