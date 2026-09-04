# Helm Best Practices

## 1. Do Not Hardcode Values

Bad:

```yaml
replicas: 5
image: nginx:1.25

Better:

replicas: {{ .Values.replicaCount }}
2. Use Separate Values Files
values.yaml
values-dev.yaml
values-test.yaml
values-prod.yaml
3. Pin Versions

Avoid:

image: nginx:latest

Use:

image: nginx:1.25.4
4. Validate Before Deployment
helm lint ./myapp

helm template myapp ./myapp

helm upgrade --install myapp ./myapp \
--dry-run --debug
5. Use Version Control

Store:

Helm Charts
values.yaml
Environment-specific values

in Git.

6. Do Not Store Plaintext Secrets

Do not put real passwords directly in:

values.yaml

Use a proper secret-management solution when possible.