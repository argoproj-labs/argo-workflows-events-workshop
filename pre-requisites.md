# Pre-Requisites
### Install Kubenetes on local
1. Install Kubernetes locally (use Docker on Desktop + K3D as it supports RBAC):
2. Clone  https://github.com/argoproj-labs/advanced-argo-workflows-workshop.git
3. Run `kubectl`
4. Run `brew install k3d`
5. Run `k3d create`
6. Run `export KUBECONFIG="$(k3d get-kubeconfig --name='k3s-default')"`
7. Run `kubectl cluster-info`

### Install Argo workflow controller
1. Run `kubectl create ns argo`
2. Run `kubectl -n argo apply -f https://raw.githubusercontent.com/argoproj/argo-workflows/master/manifests/quick-start-postgres.yaml`
3. Run `kubectl -n argo patch cm workflow-controller-configmap -p '{"data": {"containerRuntimeExecutor": "pns"}}' ;# needed for K3S`
4. Run `kubectl -n argo get pods`
5. Run `kubectl -n argo port-forward svc/argo-server 2746:2746`
6. Open in Browser http://localhost:2746 
7. Run `brew install argoproj/tap/argo`

### Verify the installation
1. Run `argo list`
2. Run `argo submit https://raw.githubusercontent.com/argoproj/argo-workflows/master/examples/hello-world.yaml --watch` 

![image](https://user-images.githubusercontent.com/33908564/128098762-42814586-9b42-465c-aabf-3b5de09c8408.png)
