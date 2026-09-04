# LoadBalancer Service

A `LoadBalancer` Service exposes an application externally using a load balancer.

This is commonly used with cloud providers.

## Architecture

```text
Internet
   ↓
Cloud Load Balancer
   ↓
Kubernetes Service
   ↓
┌──────┬──────┬──────┐
│ Pod1 │ Pod2 │ Pod3 │
└──────┴──────┴──────┘
```

## Example

```yaml
apiVersion: v1
kind: Service

metadata:
  name: nginx-service

spec:
  selector:
    app: nginx

  ports:
    - port: 80
      targetPort: 80

  type: LoadBalancer
```

When running on a supported cloud platform, Kubernetes can work with the cloud integration to provision an external load balancer.

## Use Cases

* Public applications
* APIs
* External services

## Interview Answer

> A LoadBalancer Service exposes an application externally and integrates with the underlying infrastructure or cloud provider to provide external traffic access.
