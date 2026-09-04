# Service YAML Explained

Example:

```yaml
apiVersion: v1
kind: Service

metadata:
  name: nginx-service

spec:
  selector:
    app: nginx

  ports:
    - name: http
      protocol: TCP
      port: 80
      targetPort: 8080

  type: ClusterIP
```

## Important Fields

### name

```yaml
name: nginx-service
```

The name used to access the Service.

---

### selector

```yaml
selector:
  app: nginx
```

Selects Pods with:

```yaml
labels:
  app: nginx
```

---

### port

```yaml
port: 80
```

The port exposed by the Service.

---

### targetPort

```yaml
targetPort: 8080
```

The port on the container that receives traffic.

---

### type

```yaml
type: ClusterIP
```

Defines how the Service is exposed.

Common types:

```text
ClusterIP
NodePort
LoadBalancer
```

## Create Service

```bash
kubectl apply -f service.yaml
```

## Check Service

```bash
kubectl get svc
```

## Detailed Information

```bash
kubectl describe svc nginx-service
```
