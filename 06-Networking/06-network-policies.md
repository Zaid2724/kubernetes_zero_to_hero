# Network Policies

By default, communication rules depend on the network plugin and cluster configuration.

A NetworkPolicy allows you to define which traffic is allowed between workloads.

## Example

```text
Frontend
    ↓ Allowed
Backend
    ↓
Database
```

You can restrict:

* Ingress traffic
* Egress traffic

## Example Concept

Allow only:

```text
Frontend → Backend
```

Block:

```text
Other Pods → Backend
```

## Important

NetworkPolicy enforcement requires a CNI/network implementation that supports it.

## Interview Answer

> A NetworkPolicy is used to control allowed ingress and egress traffic for Pods based on selectors and policy rules.
