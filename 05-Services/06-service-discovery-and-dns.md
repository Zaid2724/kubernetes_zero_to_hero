# Service Discovery and DNS

Kubernetes provides internal service discovery.

Suppose you create a Service:

```text
backend-service
```

Another Pod can access it using:

```text
backend-service
```

A more complete DNS format is:

```text
backend-service.namespace.svc.cluster.local
```

## Example

```text
Frontend Pod
      ↓
http://backend-service
      ↓
Backend Service
      ↓
Backend Pods
```

## Why DNS is Important

Applications do not need to know the IP addresses of backend Pods.

They communicate using a stable Service name.

## Interview Answer

> Kubernetes uses cluster DNS for service discovery. Applications can communicate using the Service name instead of depending on dynamic Pod IP addresses.
