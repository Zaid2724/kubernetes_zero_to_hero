# How Does a Deployment Work?

A Deployment follows the desired-state model.

Example:

```yaml
replicas: 3
image: nginx:1.25
```

Kubernetes tries to maintain:

```text
3 Pods running nginx:1.25
```

## When You Create a Deployment

```text
kubectl apply
      ↓
API Server
      ↓
Deployment created
      ↓
ReplicaSet created
      ↓
Pods created
```

## When a Pod Fails

```text
3 Pods Running
      ↓
1 Pod fails
      ↓
2 Pods Running
      ↓
ReplicaSet creates a new Pod
      ↓
3 Pods Running
```

## When the Image Changes

```text
nginx:1.25
      ↓
Update Deployment
      ↓
New ReplicaSet created
      ↓
New Pods created
      ↓
Old Pods removed
```

The Deployment controls this process.
