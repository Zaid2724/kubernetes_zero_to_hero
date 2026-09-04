# What is RBAC?

RBAC stands for Role-Based Access Control.

It is used to control access to Kubernetes resources.

Example:

Developer can:

- View Pods
- View Services

Developer cannot:

- Delete Nodes
- Delete Namespaces

RBAC decides whether a request is allowed or denied.
Simple Example
Developer
    ↓
Requests: kubectl delete pod nginx
    ↓
Kubernetes API Server
    ↓
Check RBAC Permissions
    ↓
Allowed / Denied

Interview answer:

RBAC is a Kubernetes authorization mechanism that controls who can perform specific actions on specific resources.