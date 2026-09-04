# RoleBinding vs ClusterRoleBinding

Roles define permissions.

Bindings assign those permissions.

This is where many beginners get confused.

Role
│
│ Defines permissions
│
▼

RoleBinding
│
│ Assigns permissions
│
▼

User / Group / ServiceAccount
RoleBinding

Assigns permissions inside a Namespace.

Example:

User: zaid

Namespace: development

Permission:
Read Pods

Example YAML:

apiVersion: rbac.authorization.k8s.io/v1
kind: RoleBinding

metadata:
  name: read-pods
  namespace: development

subjects:
- kind: User
  name: zaid

roleRef:
  kind: Role
  name: pod-reader
  apiGroup: rbac.authorization.k8s.io
ClusterRoleBinding

Assigns a ClusterRole across the cluster.

Example:

Admin
   ↓
ClusterRoleBinding
   ↓
ClusterRole
   ↓
Cluster-wide permissions

Example:

apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRoleBinding

metadata:
  name: cluster-admin-binding

subjects:
- kind: User
  name: admin-user

roleRef:
  kind: ClusterRole
  name: cluster-admin
  apiGroup: rbac.authorization.k8s.io
RoleBinding vs ClusterRoleBinding
RoleBinding	ClusterRoleBinding
Namespace scope	Cluster-wide scope
Assigns permissions within Namespace	Assigns permissions across cluster
Can reference Role or ClusterRole	References ClusterRole
Important Point

A RoleBinding can reference a ClusterRole.

Example:

ClusterRole
     ↓
RoleBinding
     ↓
Permissions only inside selected Namespace