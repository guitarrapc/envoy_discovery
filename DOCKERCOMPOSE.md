```shell
docker-compose pull
docker-compose up --build
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
curl -X PUT "http://localhost:8080/edsservice/myservice" -H "accept: application/json" -H "Content-Type: application/json" -d "{ \"hosts\": [ { \"ip_address\": \"127.0.0.1\", \"port\": 8081, \"tags\": { \"az\": \"us-central1-a\", \"canary\": false, \"load_balancing_weight\": 50 } }, { \"ip_address\": \"127.0.0.1\", \"port\": 8082, \"tags\": { \"az\": \"us-central1-a\", \"canary\": false, \"load_balancing_weight\": 50 } }, { \"ip_address\": \"127.0.0.1\", \"port\": 8083, \"tags\": { \"az\": \"us-central1-a\", \"canary\": false, \"load_balancing_weight\": 50 } } ]}"
# ./envoy -c envoy_config.yaml -l debug
./envoy -c envoy_config.yaml
./envoy -c envoy_config_grpc.yaml
for i in {0..99}; do echo "$(curl -s http://localhost:10000)"; done | sort | uniq -c
for i in {0..9}; do echo "$(curl -s http://localhost:10000)"; done | sort | uniq -c
for i in {0..9}; do echo "$(curl -s -H 'x-selector: 1' http://localhost:10000)"; done | sort | uniq -c
for i in {0..9}; do echo "$(curl -s -H 'x-selector: 2' http://localhost:10000)"; done | sort | uniq -c
for i in {0..9}; do echo "$(curl -s -H 'x-selector: 3' http://localhost:10000)"; done | sort | uniq -c
```