# ClusterIP Service

`ClusterIP` is the default Service type.

It exposes an application only inside the Kubernetes cluster.

## Architecture

```text
Frontend Pod
      ↓
ClusterIP Service
      ↓
Backend Pods
```

External users normally cannot directly access a ClusterIP Service.

## Example

```yaml
apiVersion: v1
kind: Service

metadata:
  name: backend-service

spec:
  selector:
    app: backend

  ports:
    - protocol: TCP
      port: 80
      targetPort: 8080

  type: ClusterIP
```

## Port vs TargetPort

```text
Service Port: 80
       ↓
Pod Container Port: 8080
```

```text
Client → Service:80 → Pod:8080
```

## Use Cases

* Frontend to backend communication
* Microservices
* Internal APIs
* Database access within the cluster

## Interview Answer

> ClusterIP exposes a Service internally within the Kubernetes cluster and is commonly used for communication between applications and microservices.
