# Build and run docker image locally

```bash

# make sure you have JDK17 installed
./gradlew build clean

docker buildx build --platform linux/amd64 -t stirling-pdf -f ./Dockerfile .

docker run -d -p 8080:8080 -v ./data/tessdata:/usr/share/tessdata -v ./data/extraConfigs:/configs -v ./data/logs:/logs -e DOCKER_ENABLE_SECURITY=false -e INSTALL_BOOK_AND_ADVANCED_HTML_OPS=false --name stirling-pdf stirling-pdf
```

# Deploy to kubernetes

```bash
alias k=kubectl
k apply -f k8s/manifests
```

# Portforwarding

```bash
alias k=kubectl
k -n stirling port-forward svc/stirling-pdf 8080:80
```

