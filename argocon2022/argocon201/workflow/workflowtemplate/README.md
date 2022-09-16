
## Workflow Template Workshop
### create workflowtemplate 

```sh
argo template create  https://raw.githubusercontent.com/argoproj-labs/argo-workflows-events-workshop/main/argocon2022/argocon201/workflow/workflowtemplate/workflow-template.yaml
```

Output
```
Name:                add-example-template
Namespace:           argo
Created:             Wed Sep 14 20:34:09 -0700 (now)

```

### Submit Workflow Template

#### Workflow Level

```sh
argo submit https://raw.githubusercontent.com/argoproj-labs/argo-workflows-events-workshop/main/argocon2022/argocon201/workflowtemplate/workflow-level-ref.yaml --watch
```

Output
```
Name:                add-example-r4fst
Namespace:           argo
ServiceAccount:      default
Status:              Pending
Created:             Wed Sep 14 20:38:23 -0700 (15 seconds ago)
Progress:            

This workflow does not have security context set. You can run your workflow pods more securely by setting it.
Learn more at https://argoproj.github.io/argo-workflows/workflow-pod-security-context/

```

#### Template Level

```
argo submit https://raw.githubusercontent.com/argoproj-labs/argo-workflows-events-workshop/main/argocon2022/argocon201/workflow/workflowtemplate/template-level-ref.yaml --watch
```

Output
```
Name:                workflow-template-add-four-82nm4
Namespace:           argo
ServiceAccount:      default
Status:              Running
Conditions:          
 PodRunning          False
Created:             Wed Sep 14 21:03:11 -0700 (6 seconds ago)
Started:             Wed Sep 14 21:03:11 -0700 (6 seconds ago)
Duration:            6 seconds
Progress:            0/1

STEP                                 TEMPLATE                      PODNAME                                      DURATION  MESSAGE
 ● workflow-template-add-four-82nm4  whalesay                                                                                              
 └───◷ call-addfour-template         add-example-template/addfour  workflow-template-add-four-82nm4-3049778637  6s        PodInitializing
```

###Submiting using --from option in CLI

```
 argo submit --from workflowtemplate/add-example-template --watch
 ```


