# Service Networking

Pods are temporary and their IP addresses can change.

A Service provides a stable endpoint.

```text
Frontend Pod
      ↓
backend-service
      ↓
Backend Pods
```

Example:

```text
Client
   ↓
Service:80
   ↓
Pod:8080
```

## Important Fields

```yaml
ports:
  - port: 80
    targetPort: 8080
```

```text
port       → Service port
targetPort → Application/Pod port
```

The Service finds backend Pods using labels and selectors.

```text
Service Selector
app=backend
      ↓
Matching Pods
app=backend
```
