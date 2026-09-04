# ReplicaSet vs Deployment

This is a common interview question.

| ReplicaSet                                      | Deployment                               |
| ----------------------------------------------- | ---------------------------------------- |
| Maintains Pod replicas                          | Manages ReplicaSets                      |
| Provides self-healing                           | Provides self-healing                    |
| Supports basic scaling                          | Supports scaling                         |
| No deployment strategy management               | Supports rolling updates                 |
| No deployment rollback management               | Supports rollbacks                       |
| Usually managed directly only in specific cases | Common choice for stateless applications |

## Architecture

```text
Deployment
     ↓
ReplicaSet
     ↓
Pods
```

## Example During an Update

Initial version:

```text
Deployment
     ↓
ReplicaSet v1
     ↓
3 Pods running app:v1
```

After updating the application:

```text
Deployment
├── ReplicaSet v1 → Old Pods scaled down
│
└── ReplicaSet v2 → New Pods running app:v2
```

The Deployment manages this update process.

## Which Should You Use?

For most stateless production applications:

```text
Use Deployment
```

The Deployment automatically manages ReplicaSets.

## Interview Answer

> A ReplicaSet ensures that a specified number of Pod replicas are running. A Deployment is a higher-level object that manages ReplicaSets and adds features such as rolling updates and rollbacks.
