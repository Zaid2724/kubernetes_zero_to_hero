# RBAC Practical Examples
Example 1: Developer Can Only Read Pods
apiVersion: rbac.authorization.k8s.io/v1
kind: Role

metadata:
  name: developer-read-pods
  namespace: development

rules:
- apiGroups: [""]
  resources:
  - pods
  verbs:
  - get
  - list
  - watch

Bind it:

apiVersion: rbac.authorization.k8s.io/v1
kind: RoleBinding

metadata:
  name: developer-read-binding
  namespace: development

subjects:
- kind: User
  name: developer1

roleRef:
  kind: Role
  name: developer-read-pods
  apiGroup: rbac.authorization.k8s.io

Result:

developer1

Can:
✓ get pods
✓ list pods
✓ watch pods

Cannot:
✗ delete pods
✗ create pods
Example 2: ServiceAccount Can Read ConfigMaps
apiVersion: rbac.authorization.k8s.io/v1
kind: Role

metadata:
  name: configmap-reader
  namespace: development

rules:
- apiGroups: [""]
  resources:
  - configmaps
  verbs:
  - get
  - list

Bind it to a ServiceAccount.