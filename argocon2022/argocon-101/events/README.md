# Hands-On Steps for ArgoCon 101 - Triggering Argo Workflows using Argo Events

1. Create EventBus
 
```kubectl apply -n argo-events -f https://raw.githubusercontent.com/argoproj-labs/argo-workflows-events-workshop/master/argocon2022/argocon-101/events/eventBus.yaml```

2. Wait for 3 Pods called “eventbus-default-js-<index>” to be in Running state

  ```kubectl -n argo-events get pods```
  
3. Create EventSource
  
```kubectl apply -n argo-events -f https://raw.githubusercontent.com/argoproj-labs/argo-workflows-events-workshop/master/argocon2022/argocon-101/events/eventSource.yaml```
  
4. Verify EventSource Pod is in Running state (should see pod prefixed by “webhook-eventsource-”)
  
```kubectl -n argo-events get pods```
  
5. Create Sensor
  
```kubectl apply -n argo-events -f https://raw.githubusercontent.com/argoproj-labs/argo-workflows-events-workshop/master/argocon2022/argocon-101/events/sensor.yaml```
  
6. Verify Sensor Pod is in Running state (should see pod prefixed by “webhook-sensor")
  
```kubectl -n argo-events get pods```
  
7. Port forward your EventSource Pod so you can access the HTTP endpoint
  
```kubectl -n argo-events port-forward $(kubectl -n argo-events get pod -l eventsource-name=webhook -o name) 12000:12000 &``` (and hit enter)
  
8. Now trigger it
  
```curl -d '{"message":"this is my first webhook"}' -H "Content-Type: application/json" -X POST http://localhost:12000/example```
  
9. Verify it worked
  
```kubectl -n argo-events get workflows | grep "webhook"```

