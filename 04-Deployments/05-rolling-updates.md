# Rolling Updates

A rolling update updates an application gradually instead of deleting all old Pods at once.

## Example

Current version:

```text
Pod 1 → app:v1
Pod 2 → app:v1
Pod 3 → app:v1
```

Update to:

```text
app:v2
```

Kubernetes gradually creates new Pods and removes old Pods.

```text
v1 v1 v1
    ↓
v2 v1 v1
    ↓
v2 v2 v1
    ↓
v2 v2 v2
```

## Update Image

```bash
kubectl set image deployment/nginx-deployment \
nginx=nginx:1.27
```

## Check Rollout

```bash
kubectl rollout status deployment/nginx-deployment
```

## Important

Rolling updates help reduce downtime during application upgrades.
