# Kubernetes Resource Management

Kubernetes allows you to define CPU and memory requirements for containers.

The two important concepts are:

```text
Requests
Limits
```

## Requests

The minimum CPU and memory requested by a container for scheduling purposes.

## Limits

The maximum resource usage allowed for a container.

Example:

```yaml
resources:
  requests:
    cpu: "250m"
    memory: "256Mi"

  limits:
    cpu: "500m"
    memory: "512Mi"
```

## CPU

```text
1000m = 1 CPU core
```

Example:

```text
250m = 0.25 CPU
500m = 0.5 CPU
```

## Important Problems

### Memory Limit Exceeded

```text
Container uses too much memory
        ↓
OOMKilled
```

### CPU Limit Exceeded

The container may be throttled.

## Why This Matters

Requests help the scheduler decide where a Pod can run.

Limits help control excessive resource usage.

## Interview Answer

> Resource requests define the resources used by Kubernetes for scheduling, while limits define the maximum CPU or memory available to a container.
