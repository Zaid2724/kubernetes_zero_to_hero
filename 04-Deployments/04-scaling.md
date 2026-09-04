# Scaling Deployments

Scaling means increasing or decreasing the number of Pods.

## Scale Up

```bash
kubectl scale deployment nginx-deployment --replicas=5
```

Result:

```text
3 Pods
   ↓
Scale to 5
   ↓
5 Pods
```

## Scale Down

```bash
kubectl scale deployment nginx-deployment --replicas=2
```

Result:

```text
5 Pods
   ↓
Scale to 2
   ↓
2 Pods
```

## Scale Using YAML

Change:

```yaml
replicas: 3
```

To:

```yaml
replicas: 5
```

Then:

```bash
kubectl apply -f deployment.yaml
```

## Production

Manual scaling is useful for testing.

For automatic scaling, use:

```text
HPA → Horizontal Pod Autoscaler
```

HPA commonly scales a Deployment based on CPU, memory, or other metrics.