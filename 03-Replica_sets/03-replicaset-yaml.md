# Creating a ReplicaSet

Example ReplicaSet:

```yaml
apiVersion: apps/v1
kind: ReplicaSet

metadata:
  name: nginx-replicaset

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

## YAML Breakdown

### apiVersion

```yaml
apiVersion: apps/v1
```

Defines the Kubernetes API version.

### kind

```yaml
kind: ReplicaSet
```

Creates a ReplicaSet.

### replicas

```yaml
replicas: 3
```

Defines the desired number of Pods.

### selector

```yaml
selector:
  matchLabels:
    app: nginx
```

Defines which Pods are managed by the ReplicaSet.

### template

The Pod template defines how new Pods should be created.

```yaml
template:
  metadata:
    labels:
      app: nginx
```

The Pod labels must match the ReplicaSet selector.

## Create

```bash
kubectl apply -f replicaset.yaml
```

## Verify

```bash
kubectl get replicasets
kubectl get pods
```

Short form:

```bash
kubectl get rs
```

## Detailed Information

```bash
kubectl describe rs nginx-replicaset
```

## Delete

```bash
kubectl delete rs nginx-replicaset
```
