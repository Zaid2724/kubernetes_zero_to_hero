# Helm vs Kustomize

Helm and Kustomize solve different problems.

| Helm | Kustomize |
|---|---|
| Package manager | Configuration customization |
| Uses templates | Uses overlays/patches |
| Uses values.yaml | Uses kustomization.yaml |
| Supports releases | No Helm-style release management |
| Good for reusable applications | Good for environment customization |
Simple Example

Helm:

Template
   +
values.yaml
   ↓
Kubernetes YAML

Kustomize:

Base YAML
   +
Dev Overlay
   ↓
Dev Configuration