# Helm Interview Questions
1. What is Helm?

Helm is a package manager for Kubernetes that packages Kubernetes resources into reusable units called Charts.

2. What is a Helm Chart?

A Helm Chart is a collection of templates and configuration files used to deploy an application to Kubernetes.

3. What is a Helm Release?

A Release is an installed instance of a Helm Chart.

Chart = Package

Release = Installed instance
4. What is values.yaml?

It contains default configuration values used by Helm templates.

Example:

replicaCount: 3

Template:

replicas: {{ .Values.replicaCount }}
5. What happens during helm install?
Helm Chart
    ↓
Read values.yaml
    ↓
Render templates
    ↓
Generate Kubernetes manifests
    ↓
Send resources to Kubernetes API
    ↓
Release created
6. What is the difference between helm install and helm upgrade?
helm install
→ Creates a new release.

helm upgrade
→ Updates an existing release.
7. How do you rollback a Helm deployment?
helm history myapp

helm rollback myapp <revision>
8. How do you check generated Kubernetes YAML?
helm template myapp ./myapp
9. How do you troubleshoot a failed Helm deployment?
1. helm status
2. helm history
3. helm lint
4. helm template
5. --dry-run --debug
6. kubectl get pods
7. kubectl describe pod
8. kubectl logs
10. Helm 2 vs Helm 3?

The key difference:

Helm 2 → Used Tiller inside the cluster.

Helm 3 → Removed Tiller.

Helm 3 communicates with Kubernetes using the user's configured access and permissions.