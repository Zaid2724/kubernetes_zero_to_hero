# Kubernetes RBAC - Zero to Hero

RBAC stands for Role-Based Access Control.

RBAC controls:

- Who can access the Kubernetes cluster?
- What resources can they access?
- What actions can they perform?

Main components:

User / ServiceAccount
        ↓
Role / ClusterRole
        ↓
RoleBinding / ClusterRoleBinding
        ↓
Permissions
Core Concept
WHO?
│
├── User
├── Group
└── ServiceAccount

WHAT CAN THEY DO?
│
├── Role
└── ClusterRole

HOW ARE PERMISSIONS ASSIGNED?
│
├── RoleBinding
└── ClusterRoleBinding

RBAC Complete Picture

Memorize this diagram:

                    ┌───────────────┐
                    │ User / App    │
                    └───────┬───────┘
                            │
                            ▼
                    ┌───────────────┐
                    │ Authentication│
                    └───────┬───────┘
                            │
                            ▼
                    ┌───────────────┐
                    │ Authorization │
                    │     RBAC      │
                    └───────┬───────┘
                            │
              ┌─────────────┴─────────────┐
              ▼                           ▼
           Role                       ClusterRole
              │                           │
              └─────────────┬─────────────┘
                            ▼
              RoleBinding / ClusterRoleBinding
                            │
                            ▼
                  User / Group / ServiceAccount
                            │
                            ▼
                       ALLOW / DENY
RBAC in One Minute
User / ServiceAccount
        ↓
Needs Permission
        ↓
Role or ClusterRole
defines WHAT is allowed
        ↓
RoleBinding or ClusterRoleBinding
assigns the permission
        ↓
Kubernetes allows or denies the request