# Pod Architecture

A Pod runs on a Kubernetes Node.

```text
Kubernetes Cluster
│
├── Node 1
│   ├── Pod A
│   │   └── Container
│   │
│   └── Pod B
│       ├── App Container
│       └── Sidecar Container
│
└── Node 2
    └── Pod C
        └── Container
```

## What does a Pod provide?

### 1. Shared Network

Containers inside the same Pod share the same network namespace.

Example:

```text
Pod IP: 10.244.1.5

App Container
localhost:8080

Sidecar Container
localhost:9090
```

The containers can communicate using:

```text
localhost
```

### 2. Shared Storage

Containers can share volumes.

```text
Pod
│
├── App Container
│      │
│      └── /data
│
└── Sidecar Container
       │
       └── /data
```

### 3. Shared Lifecycle

Containers in a Pod are scheduled together.

If a Pod is scheduled:

```text
Node
  ↓
Pod
  ↓
All containers inside the Pod
```

## Important Concept

A Pod is **not equal to a container**.

```text
Pod
 ├── Container
 ├── Container
 └── Container
```

However, the recommended pattern is:

```text
One Pod = One Main Application
```

Additional containers should support the main application.
