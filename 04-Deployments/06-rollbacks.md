# Deployment Rollbacks

If a new application version has problems, Kubernetes can roll back to a previous revision.

## Check History

```bash
kubectl rollout history deployment/nginx-deployment
```

## Roll Back

```bash
kubectl rollout undo deployment/nginx-deployment
```

## Roll Back to a Specific Revision

```bash
kubectl rollout undo deployment/nginx-deployment --to-revision=2
```

## Example

```text
Version 1 → Working
       ↓
Version 2 → Deployed
       ↓
Application failure
       ↓
Rollback
       ↓
Version 1 restored
```

## Important

Rollbacks work because Deployments maintain ReplicaSet revision history.

The number of old ReplicaSets retained is controlled by:

```yaml
revisionHistoryLimit: 10
```
