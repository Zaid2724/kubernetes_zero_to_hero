# Kubernetes Services

A **Service** provides a stable network endpoint to access one or more Pods.

## Why Do We Need Services?

Pods are temporary.

```text
Pod created → IP: 10.10.1.5

Pod deleted

New Pod created → IP: 10.10.2.8
```

If applications directly communicate using Pod IP addresses, communication can break.

A Service provides a stable:

* IP address
* DNS name
* Endpoint

## Basic Architecture

```text
Client
   ↓
Service
   ↓
┌──────┬──────┬──────┐
│ Pod1 │ Pod2 │ Pod3 │
└──────┴──────┴──────┘
```

## Main Service Types

| Type         | Usage                                       |
| ------------ | ------------------------------------------- |
| ClusterIP    | Internal communication                      |
| NodePort     | Access through Node IP and port             |
| LoadBalancer | External access using a cloud load balancer |

## Important Concept

A Service identifies Pods using:

```text
Labels + Selectors
```

Example:

```text
Service Selector:
app=nginx

        ↓

Matching Pods:
app=nginx
```
Interview Answer

A Kubernetes Service provides a stable network endpoint and DNS name for accessing a group of Pods. It uses labels and selectors to identify the Pods that should receive traffic.