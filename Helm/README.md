# Helm - Kubernetes Package Manager

Helm helps us package, configure, install, upgrade,
and manage Kubernetes applications.

Without Helm:

deployment.yaml
service.yaml
configmap.yaml
ingress.yaml

With Helm:

Helm Chart
    ↓
helm install
    ↓
Kubernetes Resources
Core Concepts
Chart     = Application package/template
Values    = Configuration
Template  = Dynamic Kubernetes YAML
Release   = Installed instance of a Chart
Repository = Location where Charts are stored

Complete Flow
Helm Chart
    │
    ├── templates/
    ├── values.yaml
    └── Chart.yaml
            │
            ▼
       helm install
            │
            ▼
     Render Templates
            │
            ▼
   Kubernetes YAML Manifests
            │
            ▼
     Kubernetes API Server
            │
            ▼
         Resources

Helm in 30 Seconds
Chart
= Application package.

values.yaml
= Configuration.

Templates
= Dynamic Kubernetes YAML.

Release
= Installed Chart.

helm install
= Deploy.

helm upgrade
= Update.

helm rollback
= Revert.