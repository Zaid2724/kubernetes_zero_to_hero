# ServiceAccount with RBAC

Applications running inside Kubernetes may need
to communicate with the Kubernetes API.

Example:

Monitoring Application
        ↓
Needs access to
        ↓
Pods and Nodes

We use:

ServiceAccount
       ↓
Role / ClusterRole
       ↓
RoleBinding / ClusterRoleBinding
       ↓
Kubernetes API
Create ServiceAccount
apiVersion: v1
kind: ServiceAccount

metadata:
  name: monitoring-sa
  namespace: monitoring
Assign ClusterRole
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRoleBinding

metadata:
  name: monitoring-binding

subjects:
- kind: ServiceAccount
  name: monitoring-sa
  namespace: monitoring

roleRef:
  kind: ClusterRole
  name: view
  apiGroup: rbac.authorization.k8s.io
Attach ServiceAccount to Pod
spec:
  serviceAccountName: monitoring-sa

Final flow:

Pod
 ↓
ServiceAccount
 ↓
RBAC Permission
 ↓
Kubernetes API