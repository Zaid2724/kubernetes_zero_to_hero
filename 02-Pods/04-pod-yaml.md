# Creating a Pod Using YAML

A basic Pod definition:

```yaml
apiVersion: v1
kind: Pod

metadata:
  name: nginx-pod
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

Defines the Kubernetes API version.

```yaml
apiVersion: v1
```

### kind

Defines the Kubernetes object.

```yaml
kind: Pod
```

### metadata

Contains information about the object.

```yaml
metadata:
  name: nginx-pod
  labels:
    app: nginx
```

### spec

Defines the desired configuration.

```yaml
spec:
```

### containers

Defines the containers inside the Pod.

```yaml
containers:
  - name: nginx
    image: nginx:1.27
```

## Create the Pod

```bash
kubectl apply -f pod.yaml
```

## Verify

```bash
kubectl get pods
```

## Detailed Information

```bash
kubectl describe pod nginx-pod
```

## Delete

```bash
kubectl delete -f pod.yaml
```

## Important Interview Point

`kubectl apply` follows the declarative approach.

You define:

```text
Desired State
```

Kubernetes attempts to make the actual state match it.
