# Prerequisites for Argocon 101

1. Install Kubernetes locally using either:
- minikube
- kind
- k3s or k3d (we use k3d)
- Docker Desktop

2. Make sure kubectl is installed and if not install it


# Mac k3d install instructions

```
brew install k3d 
k3d cluster create
k3d kubeconfig get k3s-default > ~/Downloads/argo-workshop-k8s.config
export KUBECONFIG=~/Downloads/argo-workshop-k8s.config
kubectl cluster-info  # verify no errors
```
