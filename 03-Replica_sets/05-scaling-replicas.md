# Scaling ReplicaSets

Scaling means increasing or decreasing the number of Pod replicas.

## Scale Using kubectl

Increase to 5 Pods:

```bash
kubectl scale rs nginx-replicaset --replicas=5
```

Result:

```text
Before:

Pod 1
Pod 2
Pod 3

After:

Pod 1
Pod 2
Pod 3
Pod 4
Pod 5
```

## Scale Using YAML

Change:

```yaml
replicas: 3
```

to:

```yaml
replicas: 5
```

Then apply:

```bash
kubectl apply -f replicaset.yaml
```

## Scale Down

```bash
kubectl scale rs nginx-replicaset --replicas=2
```

The ReplicaSet removes Pods until:

```text
Desired Pods = Actual Pods
```

## Important Production Point

Manual scaling works, but production applications commonly use:

```text
HPA → Scales Pods automatically
```

In most real applications, the HPA targets a Deployment rather than managing a ReplicaSet directly.
