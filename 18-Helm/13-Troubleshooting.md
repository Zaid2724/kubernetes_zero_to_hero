# Helm Troubleshooting

## 1. Check Release

```bash
helm list
helm status <release-name>
2. Check History
helm history <release-name>
3. Render Templates
helm template <release-name> ./chart

Use this to see the final Kubernetes YAML before deployment.

4. Dry Run
helm upgrade --install myapp ./myapp \
--dry-run \
--debug
5. Validate Chart
helm lint ./myapp
Common Problems
Release Already Exists
cannot re-use a name that is still in use

Check:

helm list -A

Use another release name or remove the old release.

YAML Error

Check:

helm template myapp ./myapp

The problem is often:

Wrong indentation
Incorrect template syntax
Missing value
Upgrade Failed

Check:
helm status myapp

kubectl get pods
kubectl get events

Helm may be successful while the Kubernetes application itself fails to become healthy.