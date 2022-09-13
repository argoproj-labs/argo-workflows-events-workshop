# Hands-On Steps

1. Apply EventSource spec.

```shell
kubectl apply -f https://raw.githubusercontent.com/argoproj-labs/argo-workflows-events-workshop/main/argocon2022/argocon201/events/eventsource-filtering/es.yaml
```

2. Apply Sensor spec.

```shell
kubectl apply -f https://raw.githubusercontent.com/argoproj-labs/argo-workflows-events-workshop/main/argocon2022/argocon201/events/eventsource-filtering/sensor.yaml
```

3. Verify Pods are running.

```shell
kubectl get po
```

4. Port forward to the EventSource pod, so that we can post data to it: 

```shell
kubectl port-forward `kubectl get po -leventsource-name=filter-webhook | grep -v NAME | awk '{print $1}'` 8080
```

5. Watch Sensor pod logs.

```shell
kubectl logs -f `kubectl get po -lsensor-name=es-filter-example | grep -v NAME | awk '{print $1}'`
```

6. Post data, and check Sensor logs to verify.

```shell
curl -X POST -H "Content-Type: application/json" -d '{"name": "Derek", "department": {"id": 2, "name": "HR"}}' http://localhost:8080/example
curl -X POST -H "Content-Type: application/json" -d '{"name": "John", "department": {"id": 3, "name": "Dev"}}' http://localhost:8080/example
curl -X POST -H "Content-Type: application/json" -d '{"name": "Peter", "department": {"id": 3, "name": "Dev"}}' http://localhost:8080/example
```

7. Clean up.

```shell
kubectl delete es --all
kubectl delete sensor --all
```