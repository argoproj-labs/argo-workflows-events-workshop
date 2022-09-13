# Hands-On Steps

1. Apply EventSource spec.

```shell
kubectl apply -f https://raw.githubusercontent.com/argoproj-labs/argo-workflows-events-workshop/main/argocon2022/argocon201/events/parameters/es.yaml
```

2. Apply Sensor spec.

```shell
kubectl apply -f https://raw.githubusercontent.com/argoproj-labs/argo-workflows-events-workshop/main/argocon2022/argocon201/events/parameters/sensor.yaml
```

3. Verify Pods are running.

```shell
kubectl get po
```

4. Port forward, to post data.

```shell
kubectl port-forward `kubectl get po -leventsource-name=params-webhook | grep -v NAME | awk '{print $1}'` 8080
```

5. Watch Sensor pod logs.

```shell
kubectl logs -f `kubectl get po -lsensor-name=param-sensor | grep -v NAME | awk '{print $1}'`
```

6. Post data.

```shell
# Check the created workflow logs
curl -X POST -H "Content-Type: application/json" -d '{"msg": "Hello September"}' http://localhost:8080/example
# Check workflow logs
curl -X POST -H "Content-Type: application/json" -d '{"msg": "Hello again"}' http://localhost:8080/example
# Check workflow logs
curl -X POST -H "Content-Type: application/json" -d '{"none": "Hello"}' http://localhost:8080/example
```

7. Clean up.

```shell
kubectl delete es --all
kubectl delete sensor --all
kubectl delete wf --all
```