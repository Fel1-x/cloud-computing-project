# Discovering the Higgs Boson with Cloud Computing.

This repository outlines two approaches for a parallelised workflow of the [ATLAS Open data higgs boson discovery analysis](https://github.com/atlas-outreach-data-tools/notebooks-collection-opendata/blob/master/13-TeV-examples/uproot_python/HZZAnalysis.ipynb).

This branch contains the instructions on how to set up a Docker Compose + Swarm approach whilst the `main' branch contains a Kubernetes approach

To begin either, Docker must be installed on the machine. For the Kubernetes approach, Kubernetes must also be [enabled](https://docs.docker.com/desktop/use-desktop/kubernetes/) via Docker Desktop.

## Start Swarm

First, initalise Docker Swarm in the terminal.

```bash
docker swarm init
```

---

## Orchestrate Containers with Docker Compose

Enter this command into the terminal.

```bash
docker compose up
```

#### Troubleshooting

Only one iteration of docker compose can be used at once, thus running this command before docker compose up can repair some errors.

```bash
docker compose down
```
---


## Changing Worker Count

To alter the number of workers, edit the `docker-compose.yml` file:

```yaml
worker:
  build: worker/.
  networks:
    - rabbit
  deploy:
    mode: replicated
    replicas: 2   # change this value to the desired worker count (>1)
```
---

## Output

The plot output should be viewable, after programme completion in the `output` folder
