# Deployment Strategies

The main Deployment strategies are:

## 1. RollingUpdate

Default strategy.

Pods are gradually replaced.

```text
Old Pods → Gradually replaced → New Pods
```

Example:

```yaml
strategy:
  type: RollingUpdate
```

## 2. Recreate

All existing Pods are terminated before new Pods are created.

```text
Old Pods removed
      ↓
New Pods created
```

Example:

```yaml
strategy:
  type: Recreate
```

## RollingUpdate vs Recreate

| RollingUpdate    | Recreate               |
| ---------------- | ---------------------- |
| Gradual update   | All old Pods removed   |
| Reduced downtime | Downtime possible      |
| Default strategy | Used in specific cases |

## maxSurge

Defines how many additional Pods can be created during an update.

Example:

```yaml
maxSurge: 1
```

## maxUnavailable

Defines how many Pods can be unavailable during an update.

Example:

```yaml
maxUnavailable: 1
```

Example with 3 replicas:

```text
Desired Pods: 3

maxSurge: 1
Maximum Pods during update: 4

maxUnavailable: 1
At least 2 Pods should remain available
```
