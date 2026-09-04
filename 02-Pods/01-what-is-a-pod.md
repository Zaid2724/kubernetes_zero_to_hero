# What is a Pod?

A Pod is the smallest unit that Kubernetes creates, schedules, and manages.

A Pod can contain:

* One container
* Multiple containers

## Example

```text
Pod
 ├── Nginx Container
 └── Sidecar Container
```

The containers inside a Pod are treated as a single logical application unit.

## Why not run containers directly?

Kubernetes needs a unit that can provide shared:

* Networking
* Storage
* Lifecycle

That unit is called a Pod.

## Pod vs Container

| Container                      | Pod                                    |
| ------------------------------ | -------------------------------------- |
| Runs an application            | Runs one or more containers            |
| Created by a container runtime | Managed by Kubernetes                  |
| Has isolated processes         | Provides shared networking and volumes |
| Individual runtime unit        | Smallest Kubernetes deployment unit    |

## Simple Example

Without Kubernetes:

```text
Docker
   │
Container
```

With Kubernetes:

```text
Kubernetes
   │
  Pod
   │
Container
```

## Interview Answer

**What is a Pod?**

> A Pod is the smallest deployable unit in Kubernetes. It represents one or more containers that run together on the same Node and share networking, storage, and lifecycle.
