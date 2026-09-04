# Pod Lifecycle

A Pod goes through different phases during its lifetime.

## Pod Lifecycle

```text
Pending
   ↓
Running
   ↓
Succeeded / Failed
```

### Pending

The Pod has been accepted by Kubernetes but is not yet running.

Possible reasons:

* Image is downloading
* Scheduler is finding a Node
* Resources are unavailable

Check:

```bash
kubectl describe pod <pod-name>
```

---

### Running

The Pod has been scheduled and containers are running.

Check:

```bash
kubectl get pods
```

---

### Succeeded

All containers completed successfully.

Commonly seen with:

```text
Jobs
Batch processing
```

---

### Failed

One or more containers terminated unsuccessfully.

Check:

```bash
kubectl describe pod <pod-name>
kubectl logs <pod-name>
```

---

### Unknown

Kubernetes cannot determine the Pod's current state.

Usually caused by communication problems between:

```text
Control Plane ↔ Node
```

## Important: Pod Phase vs Container Status

Do not confuse these.

### Pod Phase

```text
Pending
Running
Succeeded
Failed
Unknown
```

### Container Status

Examples:

```text
Waiting
Running
Terminated
CrashLoopBackOff
ImagePullBackOff
OOMKilled
```

`CrashLoopBackOff` is not a Pod phase. This is a common interview question.
