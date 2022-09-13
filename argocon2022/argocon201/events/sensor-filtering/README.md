# Hands-On Steps

1. Apply EventSource spec.

```shell
kubectl apply -f https://raw.githubusercontent.com/argoproj-labs/argo-workflows-events-workshop/main/argocon2022/argocon201/events/sensor-filtering/es.yaml
```

2. Apply Sensor spec.

```shell
kubectl apply -f https://raw.githubusercontent.com/argoproj-labs/argo-workflows-events-workshop/main/argocon2022/argocon201/events/sensor-filtering/sensor.yaml
```

3. Verify Pods are running.

```shell
kubectl get po
```

4. Port forward, to post data.

```shell
kubectl port-forward `kubectl get po -leventsource-name=sensor-filter-es | grep -v NAME | awk '{print $1}'` 8080
```

5. Watch Sensor pod logs.

```shell
kubectl logs -f `kubectl get po -lsensor-name=sensor-filtering | grep -v NAME | awk '{print $1}'`
```

6. Post data.

```yaml
# Check if there’s any workflow created - should not
curl -X POST -H "Content-Type: application/json" -d '{"message": "Hello world", "value": 40}' http://localhost:8080/example
# Check workflow objects again
curl -X POST -H "Content-Type: application/json" -d '{"message": "Hello again", "value": 60}' http://localhost:8080/example
```

7. Clean up.

```shell
kubectl delete es --all
kubectl delete sensor --all
kubectl delete wf --all
```