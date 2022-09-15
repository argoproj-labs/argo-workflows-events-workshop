## Plugins

### Patch the Controller  Deploymentt

```
Kubectl apply -f  https://raw.githubusercontent.com/argoproj-labs/argo-workflows-events-workshop/main/argocon2022/argocon201/workflow/plugins/deployment-patch.yaml -n argo
```

### Register the Plugins

```
Kubectl apply -f https://raw.githubusercontent.com/argoproj-labs/argo-workflows-events-workshop/main/argocon2022/argocon201/workflow/plugins/hello-world-plugin.yaml -n argo```
```

### Submit the Workflow with Plugin
```
argo submit https://raw.githubusercontent.com/argoproj-labs/argo-workflows-events-workshop/main/argocon2022/argocon201/workflow/plugins/wf-plugin.yaml --watch
```

Output
```
<img width="721" alt="image" src="https://user-images.githubusercontent.com/33908564/190315949-33e367c5-e4b0-44d7-992c-f42d3afa234f.png">

