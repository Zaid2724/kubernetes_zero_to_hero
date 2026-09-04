# Static Pods

A Static Pod is managed directly by the kubelet instead of the Kubernetes API.

The kubelet watches a specific directory for Pod manifest files.

Example:

```text
/etc/kubernetes/manifests/
```

When a YAML file is placed in this directory:

```text
kubelet
   ↓
Detects YAML
   ↓
Creates Static Pod
```

## Important Characteristics

* Managed by kubelet
* Runs on a specific Node
* Cannot be scheduled to another Node
* API Server only displays a mirror representation

## Common Use Case

Kubernetes control plane components are commonly deployed as Static Pods.

Examples:

```text
kube-apiserver
kube-scheduler
kube-controller-manager
```

## Interview Question

**What happens if a Static Pod crashes?**

The kubelet detects that the Pod is not running and recreates it based on the manifest file.
