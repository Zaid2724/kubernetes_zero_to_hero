# Kubernetes Troubleshooting

The most important troubleshooting approach is:

```text
Status
  ↓
Describe
  ↓
Events
  ↓
Logs
  ↓
Exec
```

## Essential Commands

```bash
# Check resources
kubectl get pods
kubectl get nodes
kubectl get deployments
kubectl get svc

# Detailed information and events
kubectl describe pod <pod-name>

# Application logs
kubectl logs <pod-name>

# Logs from previous crashed container
kubectl logs <pod-name> --previous

# Enter container
kubectl exec -it <pod-name> -- sh

# Check events
kubectl get events
```

---

## Pod Pending

The Pod cannot be scheduled.

Common reasons:

* Insufficient CPU or memory
* No matching Node
* Taints
* PVC not available

Check:

```bash
kubectl describe pod <pod-name>
```

---

## CrashLoopBackOff

The container starts and repeatedly crashes.

Common reasons:

* Application error
* Wrong environment variables
* Missing configuration
* Incorrect command
* Dependency failure

Check:

```bash
kubectl logs <pod-name>
kubectl logs <pod-name> --previous
```

---

## ImagePullBackOff

Kubernetes cannot pull the container image.

Common reasons:

* Wrong image name
* Wrong tag
* Private registry authentication issue

Check:

```bash
kubectl describe pod <pod-name>
```

---

## OOMKilled

The container exceeded its memory limit.

Check:

```bash
kubectl describe pod <pod-name>
```

Review:

```text
Memory limit
Application memory usage
```

---

## Service Not Working

Check:

```text
Service
   ↓
Selector
   ↓
Pod Labels
   ↓
Endpoints / EndpointSlices
   ↓
Pod Readiness
   ↓
targetPort
```

Commands:

```bash
kubectl describe svc <service-name>
kubectl get endpointslices
kubectl get pods --show-labels
```

---

## Node NotReady

Check:

```bash
kubectl get nodes
kubectl describe node <node-name>
```

Possible causes:

* kubelet issue
* Network issue
* Resource pressure
* Container runtime issue

## Interview Answer

> My troubleshooting approach starts with resource status and events, followed by describe output, container logs, configuration validation, and network or infrastructure checks depending on the failure.
