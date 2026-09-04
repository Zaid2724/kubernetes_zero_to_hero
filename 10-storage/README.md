# Kubernetes Storage

Container storage is usually temporary.

If a Pod is deleted, data stored only inside the container can be lost.

For persistent data, Kubernetes uses persistent storage.

## Basic Flow

```text
Pod
 ↓
PVC
 ↓
PV
 ↓
Actual Storage
```

## Volume

A Volume provides storage to containers inside a Pod.

Example:

```text
Pod
├── Container 1
└── Container 2
       ↓
    Shared Volume
```

---

# PersistentVolume (PV)

A **PV** represents actual storage available to the Kubernetes cluster.

Examples:

* AWS EBS
* Azure Disk
* NFS
* Other storage systems

---

# PersistentVolumeClaim (PVC)

A **PVC** is a request for storage.

Example:

```text
Application
     ↓
Requests 10Gi Storage
     ↓
PVC
     ↓
Matching PV / Dynamically Provisioned Storage
```

## Example PVC

```yaml
apiVersion: v1
kind: PersistentVolumeClaim

metadata:
  name: app-storage

spec:
  accessModes:
    - ReadWriteOnce

  resources:
    requests:
      storage: 10Gi
```

---

# StorageClass

A StorageClass defines how storage can be dynamically provisioned.

Example:

```text
Pod
 ↓
PVC
 ↓
StorageClass
 ↓
Automatically creates storage
```

This is common in cloud environments.

## Important Access Modes

```text
ReadWriteOnce (RWO)
→ Read/write by one Node

ReadOnlyMany (ROX)
→ Read-only by multiple Nodes

ReadWriteMany (RWX)
→ Read/write by multiple Nodes
```

Actual support depends on the underlying storage provider.

## Important Commands

```bash
kubectl get pv
kubectl get pvc
kubectl get storageclass

kubectl describe pvc <pvc-name>
```

## Interview Answer

> A PersistentVolume represents storage available to the cluster, while a PersistentVolumeClaim is a request for storage made by an application. A StorageClass can dynamically provision storage based on the PVC request.
