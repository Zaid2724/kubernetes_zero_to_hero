# Kubernetes Namespaces

A **Namespace** is used to logically separate Kubernetes resources inside the same cluster.

## Example

```text
Kubernetes Cluster
│
├── default
├── development
├── staging
└── production
```

Instead of creating separate clusters for every environment, namespaces can separate resources within one cluster.

## Common Namespaces

```text
default          → Default namespace
kube-system      → Kubernetes system components
kube-public      → Public cluster resources
kube-node-lease  → Node heartbeat information
```

## Create a Namespace

```yaml
apiVersion: v1
kind: Namespace

metadata:
  name: development
```

Apply:

```bash
kubectl apply -f namespace.yaml
```

## Commands

```bash
# List namespaces
kubectl get namespaces

# Create namespace
kubectl create namespace development

# Create resources in namespace
kubectl apply -f deployment.yaml -n development

# View Pods
kubectl get pods -n development

# Delete namespace
kubectl delete namespace development
```

## Important Points

* Namespaces provide logical isolation.
* Names of most resources only need to be unique within a namespace.
* Resources can communicate across namespaces when networking and DNS allow it.
* RBAC and ResourceQuota can be applied per namespace.

## Interview Answer

> A Namespace is a logical partition within a Kubernetes cluster used to organize and isolate resources such as development, staging, and production environments.
