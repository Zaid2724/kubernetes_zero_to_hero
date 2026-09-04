# RBAC Architecture

Complete RBAC flow:

User / Application
        ↓
Authentication
        ↓
Identity Verified
        ↓
Authorization
        ↓
RBAC Checks Permissions
        ↓
Role / ClusterRole
        ↓
Binding
        ↓
Allow or Deny
Real Example

Developer runs:

kubectl delete pod nginx

Kubernetes checks:

1. Who is making this request?

2. Is the user authenticated?

3. Does the user have permission?

4. Is "delete" allowed?

5. Is the resource "pod"?

6. Is access allowed in this Namespace?

Result:

Permission exists → ALLOW

Permission does not exist → DENY