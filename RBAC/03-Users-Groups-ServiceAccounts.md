# Users, Groups and ServiceAccounts

Kubernetes permissions can be assigned to:

- Users
- Groups
- ServiceAccounts
User

A human or external identity.

Example:

Developer
Admin
DevOps Engineer

Kubernetes itself does not normally manage regular user objects internally in the same way it manages ServiceAccounts. User authentication is commonly handled through external mechanisms such as certificates or identity providers.

Group

A collection of users.

Example:

developers
devops
admins

Instead of assigning permissions to every developer:

Developer 1 → Permission
Developer 2 → Permission
Developer 3 → Permission

Use:

developers group
        ↓
      Permission
ServiceAccount

A ServiceAccount is an identity used by applications and Pods.

Example:

Pod
 │
 ▼
ServiceAccount
 │
 ▼
RBAC Permissions
 │
 ▼
Kubernetes API

Use case:

Application needs to read ConfigMaps.

Instead of giving permissions to a human user, assign permissions to the Pod's ServiceAccount.