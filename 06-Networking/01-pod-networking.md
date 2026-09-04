# Pod Networking

Each Pod receives its own IP address.

Example:

```text
Pod 1 → 10.244.1.10
Pod 2 → 10.244.2.15
```

Pods can communicate using IP addresses, but this is not recommended for application communication because Pod IPs can change.

Use Services instead.

## Same Pod Communication

Containers inside the same Pod share the network namespace.

```text
Pod
├── App Container → localhost:8080
└── Sidecar → localhost:9090
```

Containers can communicate using:

```text
localhost:<port>
```

## Pod-to-Pod Communication

```text
Pod A
  ↓
Pod B
```

Even if Pods are running on different Nodes, the Kubernetes network should allow communication.

Example:

```text
Node 1                 Node 2
Pod A  ──────────────→ Pod B
```

The CNI plugin is responsible for implementing Pod networking.
