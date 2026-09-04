# DNS and Service Discovery

Kubernetes uses DNS for service discovery.

Instead of:

```text
http://10.244.1.10:8080
```

Applications should use:

```text
http://backend-service
```

A complete DNS name can look like:

```text
backend-service.default.svc.cluster.local
```

## Traffic Flow

```text
Frontend
    ↓
backend-service
    ↓
DNS resolves Service
    ↓
Backend Pods
```

## CoreDNS

CoreDNS provides DNS functionality inside the Kubernetes cluster.

## Interview Answer

> Kubernetes service discovery allows applications to communicate using Service names instead of depending on changing Pod IP addresses.
