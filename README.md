# Discovering the Higgs Boson with Cloud Computing.

This repository outlines two approaches for a parallelised workflow of the [ATLAS Open data higgs boson discovery analysis](https://github.com/atlas-outreach-data-tools/notebooks-collection-opendata/blob/master/13-TeV-examples/uproot_python/HZZAnalysis.ipynb).

This branch contains the instructions on how to set up a Kubernetes approach whilst branch `docker-compose' contains a Docker Compose + Swarm approach.

To begin either, Docker must be installed on the machine. For the Kubernetes approach, Kubernetes must also be [enabled](https://docs.docker.com/desktop/use-desktop/kubernetes/) via Docker Desktop.

## Build Docker Images

First, build the Docker images for the worker and main services:

```bash
docker build -t felixgroup/worker:latest ./worker
docker build -t felixgroup/main:latest ./main
```

---

## Deploy to Kubernetes
