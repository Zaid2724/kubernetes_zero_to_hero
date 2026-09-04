# Helm Architecture

Modern Helm uses the Helm CLI.

Basic flow:

Developer
    │
    ▼
Helm CLI
    │
    ▼
Helm Chart
    │
    ▼
Templates + Values
    │
    ▼
Rendered Kubernetes YAML
    │
    ▼
Kubernetes API Server
Important

Helm 3 does not require Tiller.

Older Helm versions:

Helm CLI
    ↓
Tiller
    ↓
Kubernetes

Helm 3:

Helm CLI
    ↓
Kubernetes API