# ReplicaSets in Kubernetes

A **ReplicaSet** ensures that a specified number of identical Pods are running at all times.

## Basic Architecture

```text
ReplicaSet
├── Pod 1
├── Pod 2
└── Pod 3
```

Example:

```yaml
replicas: 3
```

Kubernetes will try to maintain:

```text
Desired Pods = 3
Actual Pods  = 3
```

If one Pod is deleted or fails:

```text
3 Pods
   ↓
1 Pod deleted
   ↓
2 Pods
   ↓
ReplicaSet detects the difference
   ↓
Creates a new Pod
   ↓
3 Pods
```

## Main Purpose

The main purpose of a ReplicaSet is:

> Maintain the desired number of Pod replicas.

## Important Points

* A ReplicaSet manages Pods.
* It uses labels and selectors to identify Pods.
* If the number of Pods is less than desired, it creates new Pods.
* If the number of Pods is more than desired, it removes extra Pods.
* ReplicaSets provide basic self-healing and scaling.
* In production, ReplicaSets are usually managed through Deployments.

## Architecture

```text
Deployment
    ↓
ReplicaSet
    ↓
Pods
```
