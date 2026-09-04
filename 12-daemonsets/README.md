# Kubernetes DaemonSets

A **DaemonSet** ensures that a Pod runs on every selected Node.

## Example

```text
Cluster

Node 1 → Monitoring Pod
Node 2 → Monitoring Pod
Node 3 → Monitoring Pod
```

When a new Node is added:

```text
New Node
   ↓
DaemonSet automatically creates a Pod
```

## Common Use Cases

* Log collection
* Monitoring agents
* Security agents
* Networking components

## Deployment vs DaemonSet

```text
Deployment
→ You define the number of replicas

DaemonSet
→ Usually one Pod per selected Node
```

## Commands

```bash
kubectl get daemonsets
kubectl get ds
kubectl describe daemonset <name>
```

## Interview Answer

> A DaemonSet ensures that a copy of a Pod runs on every selected Node and is commonly used for monitoring, logging, security, and networking workloads.
