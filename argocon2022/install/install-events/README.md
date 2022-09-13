# Hands-On Steps to Install Argo Events

1. create the namespace

```kubectl create ns argo-events```

2. install Argo Events Controller

```kubectl apply -n argo-events -f https://raw.githubusercontent.com/argoproj-labs/argo-workflows-events-workshop/master/argocon2022/install/install-events/install.yaml```

3. verify controller-manager is running

```kubectl -n argo-events get pods```

4. Add Kubernetes Role which will be tied to our Sensor’s Service Account to enable creating Workflows

```kubectl apply -n argo-events -f https://raw.githubusercontent.com/argoproj-labs/argo-workflows-events-workshop/master/argocon2022/install/install-events/sensor-rbac.yaml```
