## Build Docker Images

First, build the Docker images for the worker and main services, then push them to your registry:

```bash
docker build -t felixgroup/worker:latest ./worker
docker build -t felixgroup/main:latest ./main
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

### Example output

```
NAME         TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)              AGE
kubernetes   ClusterIP   10.96.0.1        <none>        443/TCP              3m12s
rabbitmq     ClusterIP   10.102.191.87    <none>        5672/TCP,15672/TCP   3m2s
webserver    NodePort    10.106.242.158   <none>        80:30641/TCP         5s
```

In this case, **30641** is the port to be added to the URL.

---

## Monitor the Main Node

To stream logs from the main analysis node:

```bash
kubectl logs -f deployment/main
```

---
