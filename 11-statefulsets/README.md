# Kubernetes StatefulSets

A **StatefulSet** is used to manage applications that require:

* Stable Pod names
* Stable network identity
* Persistent storage

## Deployment vs StatefulSet

```text
Deployment
→ Stateless applications
→ Pods can be replaced with any identity

StatefulSet
→ Stateful applications
→ Pods have stable identities
```

Example:

```text
myapp-0
myapp-1
myapp-2
```

Unlike a Deployment, these Pod names are predictable.

## Common Use Cases

* Databases
* Kafka
* Elasticsearch
* Other stateful applications

## Scaling

```text
3 Replicas

myapp-0
myapp-1
myapp-2
```

Pods are generally created and terminated in an ordered manner.

## Storage

StatefulSets commonly use a separate PVC for each Pod.

```text
myapp-0 → PVC-0
myapp-1 → PVC-1
myapp-2 → PVC-2
```

## Interview Answer

> A StatefulSet is used for stateful applications that require stable Pod identity, stable network identity, and persistent storage.
