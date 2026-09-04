# Deployment Troubleshooting

## Check Deployment

```bash
kubectl get deployments
```

Example:

```text
NAME               READY   UP-TO-DATE   AVAILABLE
nginx-deployment   2/3     3            2
```

This means the Deployment expects 3 Pods, but only 2 are currently ready.

## Describe Deployment

```bash
kubectl describe deployment nginx-deployment
```

Check:

* Events
* Replica count
* Conditions
* Image version
* Deployment strategy

## Check ReplicaSets

```bash
kubectl get rs
```

## Check Pods

```bash
kubectl get pods
```

If a Pod is failing:

```bash
kubectl describe pod <pod-name>
kubectl logs <pod-name>
```

## Check Rollout

```bash
kubectl rollout status deployment/nginx-deployment
```

## Common Problems

### Pods not becoming Ready

Check:

* Readiness probe
* Application logs
* Resource limits
* Configuration
* Dependencies

### Image update is failing

Check:

```bash
kubectl describe pod <pod-name>
```

Possible causes:

* Wrong image name
* Wrong tag
* Private registry authentication issue

### Deployment rollout stuck

Check:

```bash
kubectl rollout status deployment <deployment-name>
kubectl describe deployment <deployment-name>
kubectl get pods
```
