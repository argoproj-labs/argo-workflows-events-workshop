# Argo Workflows 101 - Workshop

1. Submit Hello World Workflow

```argo submit -n argo https://raw.githubusercontent.com/argoproj-labs/argo-workflows-events-workshop/main/argocon2022/argocon-101/workflows/hello_world.yaml```

2. Useful Argo CLI commands

```shell
argo list -n argo 

argo get -n argo <workflow-name>

argo logs -n argo <workflow-name>
```

3. Using kubectl to create Workflow (OPTIONAL)

```kubectl create -n argo -f https://raw.githubusercontent.com/argoproj-labs/argo-workflows-events-workshop/main/argocon2022/argocon-101/workflows/hello_world.yaml```

4. Submit template example

```argo submit -n argo https://raw.githubusercontent.com/argoproj-labs/argo-workflows-events-workshop/main/argocon2022/argocon-101/workflows/template_example.yaml```