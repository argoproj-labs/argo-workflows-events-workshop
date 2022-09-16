# Argo Events Workshop

## Pre-requisites

- Join Slack channel for workshop in CNCF slack (#argocon-2022-wfs-events-workshop)
- Install Kubernetes locally, using one of these:
    - minikube
    - kind
    - k3s or k3d (we use k3d)
    - Docker Desktop
- Install kubectl if not installed as part of Kubernetes install

### Using k3d on Mac

```shell
brew install k3d

# Create a cluster with default name k3s-default
k3d cluster create -i rancher/k3s:v1.21.7-k3s1

# Get kubeconfig for the cluster
k3d kubeconfig get k3s-default
```

## Installation

### Argo Workflow Installation

```shell
kubectl create ns argo

kubectl -n argo apply -f https://raw.githubusercontent.com/argoproj-labs/argo-workflows-events-workshop/master/argocon2022/install/install-workflows/quick-start-postgres.yaml

# Verify pods are running
kubectl -n argo get pods

# Install argo cli
brew install argo
# Verify
argo version
```

### Argo Events Installation

```shell
kubectl create ns argo-events 
kubectl -n argo-events apply -f https://raw.githubusercontent.com/argoproj-labs/argo-workflows-events-workshop/master/argocon2022/install/install-events/install.yaml

# Verify
kubectl -n argo-events get po
```

### Some other settings

```shell
# RBAC for Senor ServiceAccount, so that it has privileges to create workflows.
kubectl apply -f https://raw.githubusercontent.com/argoproj-labs/argo-workflows-events-workshop/master/argocon2022/install/install-events/sensor-rbac.yaml

# RBAC for Workflow ServiceAccount
kubectl apply -f https://raw.githubusercontent.com/argoproj-labs/argo-workflows-events-workshop/master/argocon2022/install/install-events/workflow-rbac.yaml
```

## Create An EventBus

An `EventBus` is requried for the workshop topics.

```shell
kubectl apply -f https://raw.githubusercontent.com/argoproj-labs/argo-workflows-events-workshop/master/argocon2022/argocon-101/events/eventBus.yaml
```