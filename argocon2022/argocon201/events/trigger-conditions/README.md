# Hands-On Steps

1. Apply EventSource spec.

```shell
kubectl apply -f https://raw.githubusercontent.com/argoproj-labs/argo-workflows-events-workshop/main/argocon2022/argocon201/events/trigger-conditions/es.yaml
```

2. Apply Sensor spec.

```shell
kubectl apply -f https://raw.githubusercontent.com/argoproj-labs/argo-workflows-events-workshop/main/argocon2022/argocon201/events/trigger-conditions/sensor.yaml
```

3. Verify Pods are running.

```shell
kubectl get po
```

4. Port forward, so that we can post data to the event source.

```shell
kubectl port-forward `kubectl get po -leventsource-name=my-webhooks | grep -v NAME | awk '{print $1}'` 8080
````

5. Watch Sensor pod logs.

```shell
kubectl logs -f `kubectl get po -lsensor-name=http-get | grep -v NAME | awk '{print $1}'`
```

6. Post data, and check the logs to see which trigger is executed.

```shell
curl -X POST -H "Content-Type: application/json" -d '{}' http://localhost:8080/example1
curl -X POST -H "Content-Type: application/json" -d '{}' http://localhost:8080/example2
```

7. Additional requirement - change conditions to `dep1 && dep2`.

8. Clean up.

```shell
kubectl delete es --all
kubectl delete sensor --all
```