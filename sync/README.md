# advanced-argo-workflows-workshop

## Run Workflow at Scale

Create semephore configmap 
`kubectl apply -f  sync/semaphore-configmap.yaml`

### Workflow Level Semaphore
Submit the 5 workflows 
`argo submit sync/semaphore-wf-level.yaml sync/semaphore-wf-level.yaml sync/semaphore-wf-level.yaml sync/semaphore-wf-level.yaml sync/semaphore-wf-level.yaml
`
### Template Level Semaphore
`argo submit https://raw.githubusercontent.com/argoproj-labs/advanced-argo-workflows-workshop/main/sync/semaphore-tmpl-level.yaml --watch`

### Workflow Level Mutex
` argo submit sync/mutex-wf-level.yaml sync/mutex-wf-level.yaml sync/mutex-wf-level.yaml sync/mutex-wf-level.yaml --watch`
