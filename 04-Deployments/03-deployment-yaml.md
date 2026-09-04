# Deployment YAML

Example:

```yaml
apiVersion: apps/v1
kind: Deployment

metadata:
  name: nginx-deployment

spec:
  replicas: 3

  selector:
    matchLabels:
      app: nginx

  template:
    metadata:
      labels:
        app: nginx

    spec:
      containers:
        - name: nginx
          image: nginx:1.27
          ports:
            - containerPort: 80
```

## Important Sections

### replicas

```yaml
replicas: 3
```

Kubernetes maintains 3 Pods.

### selector

```yaml
selector:
  matchLabels:
    app: nginx
```

Identifies the Pods managed by the Deployment.

### template

Defines how Pods should be created.

```yaml
template:
  metadata:
    labels:
      app: nginx
```

The labels must match the selector.

### containers

Defines the application container.

```yaml
containers:
  - name: nginx
    image: nginx:1.27
```

## Create Deployment

```bash
kubectl apply -f deployment.yaml
```

## Check Deployment

```bash
kubectl get deployments
```

Short form:

```bash
kubectl get deploy
```

## Check Related Resources

```bash
kubectl get rs
kubectl get pods
```
