# How Kubernetes Services Work

A Service uses a selector to find matching Pods.

## Example

Service:

```yaml
selector:
  app: backend
```

Pods:

```yaml
labels:
  app: backend
```

The Service connects to all Pods with the matching label.

## Flow

```text
Client
   ↓
backend-service
   ↓
Selector: app=backend
   ↓
┌─────────┬─────────┬─────────┐
│ Pod 1   │ Pod 2   │ Pod 3   │
│ backend │ backend │ backend │
└─────────┴─────────┴─────────┘
```

## Important Components

### Service

Provides the stable access point.

### Selector

Identifies matching Pods.

### Endpoints / EndpointSlices

Represent the actual backend Pods that can receive traffic.

## Important Point

The Service does not create Pods.

```text
Deployment → Creates and manages Pods

Service → Provides network access to Pods
```
