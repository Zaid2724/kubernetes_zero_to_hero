# NodePort Service

A `NodePort` Service exposes an application using the IP address of a Kubernetes Node and a specific port.

## Architecture

```text
External User
      ↓
NodeIP:NodePort
      ↓
Service
      ↓
Pods
```

Example:

```text
http://NodeIP:30080
```

## YAML

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
      nodePort: 30080

  type: NodePort
```

## Port Flow

```text
User
  ↓
NodeIP:30080
  ↓
Service:80
  ↓
Pod:80
```

## Important

NodePort usually uses ports in the range:

```text
30000–32767
```

## Use Cases

* Learning
* Testing
* Simple environments

For most production HTTP applications, Ingress or a cloud LoadBalancer is usually a better option.
