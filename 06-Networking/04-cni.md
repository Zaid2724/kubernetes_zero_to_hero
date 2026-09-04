# CNI - Container Network Interface

CNI is the standard interface used by Kubernetes to configure container networking.

A CNI plugin handles networking for Pods.

## Simplified Flow

```text
Pod Created
    ↓
CNI Plugin
    ↓
Network configured
    ↓
Pod receives IP address
```

Common CNI implementations include:

* Calico
* Cilium
* Flannel

## What CNI Does

Depending on the implementation, it can provide:

* Pod networking
* IP address allocation
* Routing
* Network policies

## Interview Answer

> CNI is a standard interface used by Kubernetes to configure networking for Pods. A CNI plugin provides the actual networking implementation.
