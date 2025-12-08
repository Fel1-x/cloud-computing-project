# Discovering the Higgs Boson with Cloud Computing.

This repository outlines two approaches for a parallelised workflow of the [ATLAS Open data higgs boson discovery analysis](https://github.com/atlas-outreach-data-tools/notebooks-collection-opendata/blob/master/13-TeV-examples/uproot_python/HZZAnalysis.ipynb).

This branch contains the instructions on how to set up a Docker Compose + Swarm approach whilst the `main' branch contains a Kubernetes approach

To begin either, Docker must be installed on the machine. For the Kubernetes approach, Kubernetes must also be [enabled](https://docs.docker.com/desktop/use-desktop/kubernetes/) via Docker Desktop.

## Start Swarm

First, initalise Docker Swarm.

```bash
docker swarm init
```

---

## Orchestrate Containers with Docker Compose

```bash
docker compose down
docker compose up
```

---
