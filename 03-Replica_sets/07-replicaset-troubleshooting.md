# ReplicaSet Troubleshooting

## Check ReplicaSet

```bash
kubectl get rs
```

Example:

```text
NAME                DESIRED   CURRENT   READY
nginx-replicaset    3         3         2
```

### DESIRED

Number of Pods Kubernetes wants.

### CURRENT

Number of Pods currently created.

### READY

Number of Pods ready to receive traffic.

## Detailed Information

```bash
kubectl describe rs nginx-replicaset
```

Check:

* Events
* Desired replicas
* Current replicas
* Pod selector

## Check Pods

```bash
kubectl get pods
```

If Pods are failing:

```bash
kubectl describe pod <pod-name>
kubectl logs <pod-name>
```

## Common Problems

### Desired Pods Are Not Running

Possible causes:

* Insufficient CPU or memory
* ImagePullBackOff
* Scheduling issues
* Incorrect Pod configuration

Check:

```bash
kubectl describe rs <rs-name>
kubectl get pods
kubectl describe pod <pod-name>
```

### ReplicaSet Is Not Managing Expected Pods

Check:

```text
ReplicaSet Selector
        vs
Pod Labels
```

They must match.

Example:

```text
Selector: app=nginx
Pod Label: app=nginx
```

### Pod Keeps Getting Recreated

This may not be a problem.

If a Pod managed by a ReplicaSet is deleted:

```text
Pod deleted
    ↓
ReplicaSet detects fewer replicas
    ↓
New Pod created
```

This is the expected self-healing behavior.
