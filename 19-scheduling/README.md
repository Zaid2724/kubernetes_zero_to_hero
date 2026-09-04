# Kubernetes Scheduling

The **Kubernetes Scheduler** decides which Node should run a Pod.

## Basic Flow

```text
Pod Created
    ↓
Scheduler checks Nodes
    ↓
Checks resources and rules
    ↓
Selects a suitable Node
```

## What Does the Scheduler Check?

Mainly:

* CPU and Memory availability
* Resource requests
* Node selectors
* Affinity rules
* Taints and tolerations

---

## nodeSelector

Used to schedule a Pod on a specific type of Node.

Node:

```yaml
labels:
  disktype: ssd
```

Pod:

```yaml
spec:
  nodeSelector:
    disktype: ssd
```

The Pod will be scheduled only on a Node matching that label.

---

## Node Affinity

A more flexible version of `nodeSelector`.

```text
nodeSelector
→ Simple exact matching

Node Affinity
→ Advanced matching rules
```

Types:

```text
requiredDuringSchedulingIgnoredDuringExecution
→ Must match

preferredDuringSchedulingIgnoredDuringExecution
→ Preferred but not mandatory
```

---

## Pod Affinity and Anti-Affinity

### Pod Affinity

Schedule Pods close to each other.

```text
Pod A
Pod B

→ Prefer same Node / topology
```

Useful when applications communicate frequently.

### Pod Anti-Affinity

Keep Pods separate.

```text
Node 1 → App Pod
Node 2 → App Pod
```

Useful for high availability.

---

## Taints and Tolerations

A **Taint** prevents Pods from being scheduled on a Node unless they tolerate it.

```text
Taint on Node
      ↓
Pod blocked
      ↓
Unless Pod has matching Toleration
```

Example:

```text
Taint
→ "Do not schedule normal Pods here"

Toleration
→ "This Pod is allowed here"
```

## Important Difference

```text
Node Selector / Affinity
→ Attracts Pods to Nodes

Taints
→ Repels Pods from Nodes

Tolerations
→ Allow Pods to use tainted Nodes
```

## Troubleshooting Pending Pods

```bash
kubectl get pods
kubectl describe pod <pod-name>
```

Check Events for:

* Insufficient CPU
* Insufficient Memory
* Node selector mismatch
* Untolerated taint
* Affinity rules

## Interview Answer

> Kubernetes scheduling is the process of assigning Pods to suitable Nodes based on available resources, resource requests, selectors, affinity rules, taints, and tolerations.
