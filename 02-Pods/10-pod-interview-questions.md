# Pod Interview Questions

## 1. What is a Pod?

A Pod is the smallest deployable unit in Kubernetes and contains one or more containers that share networking and storage.

---

## 2. Can a Pod contain multiple containers?

Yes. Multiple containers can run inside the same Pod when they are tightly coupled.

---

## 3. Do containers inside the same Pod have different IP addresses?

No.

They share the Pod's network namespace and IP address.

They communicate with each other using:

```text
localhost
```

---

## 4. What happens if a Pod crashes?

It depends on how the Pod is managed.

For a Deployment:

```text
Pod fails
   ↓
ReplicaSet detects missing replica
   ↓
New Pod is created
```

---

## 5. Why should we not use standalone Pods in production?

Standalone Pods do not provide features such as:

* Replica management
* Rolling updates
* Easy rollbacks
* Desired-state management through a higher-level controller

Use a Deployment, StatefulSet, DaemonSet, Job, or CronJob depending on the workload.

---

## 6. What is the difference between a Pod and a Node?

| Pod                               | Node                                 |
| --------------------------------- | ------------------------------------ |
| Runs containers                   | Runs Pods                            |
| Smallest deployable unit          | VM or physical machine               |
| Managed by Kubernetes controllers | Managed by Control Plane and kubelet |

---

## 7. What is a Static Pod?

A Pod directly managed by the kubelet using a manifest file on a Node.

---

## 8. What is an Init Container?

A container that runs before the main application containers start.

All Init Containers must complete successfully.

---

## 9. What is CrashLoopBackOff?

A container repeatedly crashes, and Kubernetes waits progressively longer before restarting it.

---

## 10. Pod Phase vs Pod Status?

Pod phases include:

```text
Pending
Running
Succeeded
Failed
Unknown
```

Statuses such as `CrashLoopBackOff` and `ImagePullBackOff` describe container waiting or failure conditions and are not Pod phases.

---

## 11. How do you troubleshoot a Pod that is not starting?

```bash
kubectl get pods
kubectl describe pod <pod-name>
kubectl get events
kubectl logs <pod-name>
kubectl logs <pod-name> --previous
```

Then check:

* Image
* Environment variables
* Secrets and ConfigMaps
* Resource availability
* Scheduling constraints
* Application logs
