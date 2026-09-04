# Deployment Interview Questions

## 1. What is a Deployment?

A Deployment manages ReplicaSets and Pods and provides declarative updates, scaling, rolling updates, and rollbacks.

---

## 2. What is the relationship between Deployment, ReplicaSet, and Pod?

```text
Deployment
     ↓
ReplicaSet
     ↓
Pods
```

---

## 3. What happens when a Pod managed by a Deployment fails?

The ReplicaSet maintains the desired number of Pods and creates a replacement.

---

## 4. What happens when you update the image in a Deployment?

The Deployment creates a new ReplicaSet and gradually replaces old Pods with Pods using the new image.

---

## 5. What is a RollingUpdate?

A deployment strategy where Pods are gradually replaced with new versions to reduce downtime.

---

## 6. What is maxSurge?

The maximum number of additional Pods that can be created above the desired replica count during a rolling update.

---

## 7. What is maxUnavailable?

The maximum number of desired Pods that can be unavailable during a rolling update.

---

## 8. How do you check Deployment status?

```bash
kubectl get deployments
kubectl rollout status deployment <name>
```

---

## 9. How do you roll back a Deployment?

```bash
kubectl rollout undo deployment <name>
```

---

## 10. Deployment vs ReplicaSet?

ReplicaSet:

> Maintains the required number of Pods.

Deployment:

> Manages ReplicaSets and provides rolling updates, rollbacks, and application lifecycle management.
