The biggest mistake in Kubernetes networking is trying to memorize CNI, kube-proxy, DNS, and CIDR ranges before understanding how traffic actually moves.

Remember this first:

Pod → Pod
Pod → Service → Pod
External User → Ingress/LoadBalancer → Service → Pod

# Kubernetes Networking

Kubernetes networking allows communication between:

* Pod to Pod
* Pod to Service
* Service to Pod
* External users to applications

## Basic Traffic Flow

```text
External User
      ↓
Ingress / LoadBalancer
      ↓
Service
      ↓
Pod
```

Inside the cluster:

```text
Pod A
  ↓
Service
  ↓
Pod B
```

## Important Rules

Kubernetes networking generally follows these principles:

1. Every Pod has its own IP address.
2. Pods should be able to communicate across Nodes.
3. Containers inside the same Pod communicate using `localhost`.
4. Services provide stable access to Pods.

## Important Components

```text
CNI
 ↓
Provides Pod networking

Service
 ↓
Provides stable access to Pods

CoreDNS
 ↓
Provides DNS and service discovery

kube-proxy / Service implementation
 ↓
Helps implement Service traffic forwarding

NetworkPolicy
 ↓
Controls allowed network traffic
```
What you actually need to remember
Pod IP
→ Temporary application endpoint

Service
→ Stable endpoint for Pods

DNS / CoreDNS
→ Find Services using names

CNI
→ Provides Pod networking

kube-proxy / Service implementation
→ Helps route Service traffic

NetworkPolicy
→ Controls allowed traffic