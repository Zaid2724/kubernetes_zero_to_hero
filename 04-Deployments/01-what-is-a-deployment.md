# What is a Deployment?

A Deployment is a higher-level Kubernetes object that manages ReplicaSets and Pods.

## Architecture

```text
Deployment
     ↓
ReplicaSet
     ↓
Pods
```

## Why do we need a Deployment?

A ReplicaSet can maintain the required number of Pods.

But a ReplicaSet alone does not provide proper application update management.

A Deployment adds:

* Rolling updates
* Rollbacks
* Deployment history
* ReplicaSet management

## Example

Current application:

```text
nginx:1.25
```

You update it to:

```text
nginx:1.26
```

The Deployment gradually replaces the old version with the new version.

## Interview Answer

> A Deployment is a Kubernetes workload resource that manages ReplicaSets and Pods. It provides declarative updates, scaling, rolling updates, and rollback capabilities for applications.
