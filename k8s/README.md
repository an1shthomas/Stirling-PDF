# Build dhcker image

```bash
docker buildx build --platform linux/amd64 -t stirling-pdf -f ./Dockerfile .

docker run -d -p 8080:8080 -v /Users/anishthomas/tmp/stirling-pdf:/usr/share/tessdata -v /Users/anishthomas/tmp/stirling-pdf/extraConfigs:/configs -v /Users/anishthomas/tmp/stirling-pdf/logs:/logs -e DOCKER_ENABLE_SECURITY=false -e INSTALL_BOOK_AND_ADVANCED_HTML_OPS=false --name stirling-pdf anishkthomas/stirling-pdf
```

# Deploy to kubernetes
```bash
k apply -f k8s/manifests
```

# Portforwarding
```bash
k -n stirling port-forward svc/stirling-pdf 8080:80
```

