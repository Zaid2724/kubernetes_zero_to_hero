# kube-proxy

kube-proxy is a Kubernetes component that helps implement Service networking on Nodes.

When traffic reaches a Service, the Service implementation forwards traffic to an appropriate backend Pod.

## Simplified Flow

```text
Client
   ↓
Service
   ↓
Service networking rules
   ↓
Backend Pod
```

Depending on the cluster configuration, kube-proxy may use implementations such as:

* iptables
* IPVS

Some Kubernetes networking setups can use alternative approaches for Service handling.

## Important Point

kube-proxy does not create Pods.

Its role is related to implementing Service network connectivity.
