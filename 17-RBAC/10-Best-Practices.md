# RBAC Best Practices

## 1. Follow Least Privilege

Do not give:

resources: ["*"]
verbs: ["*"]

unless absolutely required.

Give only required permissions.

---

## 2. Avoid cluster-admin

Do not give every user:

cluster-admin

Use specific Roles and ClusterRoles.

---

## 3. Use ServiceAccounts for Applications

Do not use human credentials inside applications.

Use:

Pod
 ↓
ServiceAccount
 ↓
RBAC
4. Separate Environments

Example:

development
testing
production

Give developers access only where required.

5. Regularly Audit Permissions

Check:

Roles
ClusterRoles
RoleBindings
ClusterRoleBindings
Unused ServiceAccounts