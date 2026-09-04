# Pod Troubleshooting

The first mistake beginners make is randomly restarting Pods.

Follow this order instead:

```text
1. Check Status
        ↓
2. Describe Pod
        ↓
3. Check Events
        ↓
4. Check Logs
        ↓
5. Check Configuration
```

## Step 1: Check Pod Status

```bash
kubectl get pods
```

Example:

```text
NAME        READY   STATUS
app-pod     0/1     CrashLoopBackOff
```

## Step 2: Describe Pod

```bash
kubectl describe pod app-pod
```

Look at:

```text
Events
Container State
Restart Count
Image
Resources
```

## Step 3: Check Logs

```bash
kubectl logs app-pod
```

If the container restarted:

```bash
kubectl logs app-pod --previous
```

---

# Common Errors

## CrashLoopBackOff

Meaning:

```text
Container Starts
    ↓
Container Crashes
    ↓
Kubernetes Restarts It
    ↓
Crashes Again
```

Common causes:

* Application error
* Wrong environment variable
* Wrong startup command
* Missing configuration
* Dependency unavailable

Commands:

```bash
kubectl logs <pod>
kubectl logs <pod> --previous
kubectl describe pod <pod>
```

---

## ImagePullBackOff

Kubernetes cannot download the container image.

Common causes:

* Wrong image name
* Wrong image tag
* Private registry authentication issue
* Network problem

Check:

```bash
kubectl describe pod <pod>
```

---

## Pending

The Pod cannot be scheduled.

Common causes:

* Insufficient CPU
* Insufficient memory
* Taints
* Node selector issue
* PVC is not bound

Check:

```bash
kubectl describe pod <pod>
```

---

## OOMKilled

The container exceeded its memory limit.

Check:

```bash
kubectl describe pod <pod>
```

Review:

```text
Memory Limit
Memory Request
Actual Application Memory Usage
```

## Production Troubleshooting Flow

```text
kubectl get pods
        ↓
kubectl describe pod
        ↓
kubectl get events
        ↓
kubectl logs
        ↓
kubectl logs --previous
        ↓
kubectl exec
```
