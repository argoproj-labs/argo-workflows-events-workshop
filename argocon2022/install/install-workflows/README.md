# Hands-On Steps to Install Argo Workflows

1. Create namespace "argo"

```kubectl create ns argo```

2. Install Workflows Controller, Argo Server, CRD definitions, and more

```kubectl -n argo apply -f https://raw.githubusercontent.com/argoproj-labs/argo-workflows-events-workshop/master/argocon2022/install/install-workflows/quick-start-postgres.yaml```

3. Make sure Pods get into a Running state

```kubectl -n argo get pods –-watch```

4. Port forward port for UI so you can navigate to it in a browser 

```kubectl -n argo port-forward svc/argo-server 2746:2746 &``` (then hit enter)

5. open https://localhost:2746 in a browser to get to UI

6. Install the Argo CLI and confirm installation

```
brew install argo
argo version 
```
