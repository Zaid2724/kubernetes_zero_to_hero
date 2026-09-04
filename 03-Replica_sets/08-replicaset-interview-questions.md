# ReplicaSet Interview Questions

## 1. What is a ReplicaSet?

A ReplicaSet is a Kubernetes controller that ensures a specified number of identical Pods are running.

---

## 2. How does a ReplicaSet identify Pods?

Using:

```text
Labels and Selectors
```

---

## 3. What happens when a Pod managed by a ReplicaSet is deleted?

The ReplicaSet detects that the actual number of Pods is lower than the desired number and creates a replacement Pod.

---

## 4. Can a ReplicaSet scale Pods?

Yes.

Example:

```bash
kubectl scale rs <rs-name> --replicas=5
```

---

## 5. ReplicaSet vs Deployment?

ReplicaSet maintains the required number of Pods.

Deployment manages ReplicaSets and provides rolling updates and rollback capabilities.

---

## 6. Why do we usually use Deployments instead of ReplicaSets?

Deployments provide additional application lifecycle management.

```text
Deployment
├── Scaling
├── ReplicaSet Management
├── Rolling Updates
└── Rollbacks
```

---

## 7. What happens if there are fewer Pods than the desired replica count?

The ReplicaSet creates additional Pods.

---

## 8. What happens if there are more Pods than the desired replica count?

The ReplicaSet terminates enough matching Pods to bring the actual count back to the desired state.

---

## 9. Can a ReplicaSet manage existing Pods?

Yes, if existing Pods match the ReplicaSet's selector and are not already controlled by another controller. This is why overlapping selectors should be avoided.

---

## 10. What is the relationship between Deployment and ReplicaSet?

```text
Deployment
     ↓ manages
ReplicaSet
     ↓ manages
Pods
```

The Deployment creates and manages ReplicaSets to control application versions and rollout behavior.
