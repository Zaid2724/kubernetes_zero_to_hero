# Services and Load Balancing

A Service can distribute traffic across multiple matching backend Pods.

## Example

```text
Client
   ↓
Service
   ├── Pod 1
   ├── Pod 2
   └── Pod 3
```

If one Pod becomes unavailable and is removed from the ready endpoints, traffic should be directed to healthy backend Pods.

## Important Point

The Service is responsible for providing a stable access point.

The actual implementation of traffic forwarding depends on the cluster networking and service proxy implementation.

## Example

```text
3 Replicas

Client Request 1 → Pod 1
Client Request 2 → Pod 2
Client Request 3 → Pod 3
```

The exact traffic distribution should not be assumed to be strict round-robin.

## Production Requirement

Use readiness probes.

```text
Pod Ready → Can receive traffic

Pod Not Ready → Removed from ready Service endpoints
```
