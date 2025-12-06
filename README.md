## Build and Push Docker Images

First, build the Docker images for the worker and main services, then push them to your registry:

```bash
docker build -t felixgroup/worker:latest ./worker
docker build -t felixgroup/main:latest ./main

docker push felixgroup/main:latest
docker push felixgroup/worker:latest
```

---

## Deploy to Kubernetes

Apply all deployment manifests in the `./deployments/` directory:

```bash
kubectl apply -f ./deployments/
```

Expose the webserver deployment via a NodePort service:

```bash
kubectl expose deployment/webserver --port 80 --type NodePort
```

Check the assigned service ports:

```bash
kubectl get svc
```

---

## Access the Webserver

Open the plotting endpoint in your browser using the NodePort assigned to the webserver:

```
http://localhost:<insert-port-from-svc-check>/plot.png
```

Replace `<insert-port-from-svc-check>` with the actual NodePort value shown in the `kubectl get svc` output.

---

## Monitor the Main Node

To stream logs from the main analysis node:

```bash
kubectl logs -f deployment/main
```

---
