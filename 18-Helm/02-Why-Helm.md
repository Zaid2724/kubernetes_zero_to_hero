# Why Helm?

A Kubernetes application may contain:

- Deployment
- Service
- ConfigMap
- Secret
- Ingress
- PVC
- ServiceAccount

Without Helm:

app/
├── deployment.yaml
├── service.yaml
├── ingress.yaml
├── configmap.yaml
└── production.yaml

You may need separate YAML files for:

Development
Testing
Production

Helm solves this using templates and values.

One Template
       +
Different values
       ↓
Dev / Test / Production

Example:

Development → replicas: 1

Production  → replicas: 5