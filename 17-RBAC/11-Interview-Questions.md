# Kubernetes RBAC Interview Questions
1. What is RBAC?

RBAC is Kubernetes authorization that controls which authenticated identities can perform which actions on which resources.

2. What is the difference between authentication and authorization?
Authentication = Who are you?

Authorization = What are you allowed to do?

Authentication happens before authorization.

3. Role vs ClusterRole?
Role
→ Namespace-scoped permissions.

ClusterRole
→ Permissions for cluster-scoped resources or reusable permissions that can be applied across namespaces.
4. RoleBinding vs ClusterRoleBinding?
RoleBinding
→ Grants permissions within a Namespace.

ClusterRoleBinding
→ Grants ClusterRole permissions cluster-wide.
5. Can RoleBinding reference ClusterRole?

Yes.

A RoleBinding can reference a ClusterRole and grant those permissions only within the RoleBinding's Namespace.

6. What is a ServiceAccount?

A ServiceAccount is an identity used by Pods and workloads to authenticate to the Kubernetes API.

7. How does a Pod access the Kubernetes API?
Pod
 ↓
ServiceAccount
 ↓
Authentication
 ↓
RBAC Authorization
 ↓
Kubernetes API
8. What are common RBAC verbs?
get
list
watch
create
update
patch
delete
9. What are API groups?

API groups organize Kubernetes APIs.

Examples:

""        → Core API group
apps      → Deployments, StatefulSets
batch     → Jobs, CronJobs
10. How do you check permissions?
kubectl auth can-i get pods

kubectl auth can-i delete pods

kubectl auth can-i create deployments