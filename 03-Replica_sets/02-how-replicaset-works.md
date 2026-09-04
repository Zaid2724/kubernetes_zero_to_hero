# How Does a ReplicaSet Work?

A ReplicaSet works using:

1. Desired replica count
2. Pod template
3. Label selector

## Example

```yaml
replicas: 3
```

The ReplicaSet wants:

```text
3 Pods
```

It checks the cluster for Pods matching its selector.

Example:

```yaml
selector:
  matchLabels:
    app: nginx
```

The ReplicaSet looks for Pods with:

```yaml
labels:
  app: nginx
```

## Working Flow

```text
ReplicaSet Created
        ↓
Checks Desired Replicas
        ↓
Finds Matching Pods
        ↓
Actual Pods = 2
Desired Pods = 3
        ↓
Creates 1 New Pod
        ↓
Actual Pods = 3
```

This process continuously runs to maintain the desired state.

## Important

The ReplicaSet does not select Pods based on their names.

It uses:

```text
Labels + Selectors
```
