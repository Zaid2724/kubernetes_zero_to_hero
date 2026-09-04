# Kubernetes Autoscaling

Kubernetes supports different types of autoscaling.

## HPA - Horizontal Pod Autoscaler

HPA increases or decreases the number of Pod replicas.

```text
High CPU / Metrics
       ↓
HPA
       ↓
More Pods
```

Example:

```text
Current Replicas: 3

High Load
   ↓

Replicas: 6
```

When load decreases:

```text
Replicas: 6
   ↓
Low Load
   ↓
Replicas: 3
```

## VPA - Vertical Pod Autoscaler

VPA adjusts CPU and memory requests for workloads.

```text
Pod
↓
More CPU / Memory
```

## Cluster Autoscaler

Adds or removes Nodes based on cluster capacity.

```text
Pods cannot be scheduled
        ↓
Cluster Autoscaler
        ↓
New Node added
```

## Simple Difference

```text
HPA
→ More or fewer Pods

VPA
→ More or fewer resources per Pod

Cluster Autoscaler
→ More or fewer Nodes
```

## Interview Answer

> HPA scales the number of Pods, VPA adjusts Pod resource requests, and Cluster Autoscaler adjusts the number of Nodes based on workload requirements.
