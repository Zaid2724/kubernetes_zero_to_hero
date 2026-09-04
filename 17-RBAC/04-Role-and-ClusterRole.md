# Role vs ClusterRole

Role and ClusterRole define permissions.

They do NOT assign permissions to users directly.
Role

A Role provides permissions inside a specific Namespace.

Example:

Namespace: development

Developer can:

- get Pods
- list Pods
- watch Pods

Example YAML:

apiVersion: rbac.authorization.k8s.io/v1
kind: Role

metadata:
  name: pod-reader
  namespace: development

rules:
- apiGroups: [""]
  resources:
  - pods
  verbs:
  - get
  - list
  - watch
ClusterRole

A ClusterRole defines permissions that can apply across the cluster or to cluster-scoped resources.

Example:

Can view:

- Nodes
- PersistentVolumes

Example:

apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRole

metadata:
  name: pod-reader

rules:
- apiGroups: [""]
  resources:
  - pods
  verbs:
  - get
  - list
  - watch
Role vs ClusterRole
Role	ClusterRole
Namespace scoped	Cluster-wide definition
Used for resources in a Namespace	Can be used cluster-wide
Cannot grant access to cluster-scoped resources	Can grant access to cluster-scoped resources
Example: Pods in dev	Example: Nodes
Easy Memory Trick
Role = Namespace

ClusterRole = Cluster