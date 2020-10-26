```
docker build -t envoy_python_rest:1.0.0 -f upstream/Dockerfile ./upstream
docker tag envoy_python_rest:1.0.0 guitarrapc/envoy_python_rest:1.0.0
docker push guitarrapc/envoy_python_rest:1.0.0
```