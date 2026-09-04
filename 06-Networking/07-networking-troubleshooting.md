# Kubernetes Networking Troubleshooting

Follow this order:

```text
1. Check Pods
       ↓
2. Check Service
       ↓
3. Check Endpoints/EndpointSlices
       ↓
4. Check DNS
       ↓
5. Check NetworkPolicy
       ↓
6. Check CNI
```

## Check Pods

```bash
kubectl get pods -o wide
```

Check:

* Pod status
* Pod IP
* Node

## Check Service

```bash
kubectl get svc
kubectl describe svc <service-name>
```

Verify:

* Selector
* Port
* targetPort

## Check Endpoints

```bash
kubectl get endpoints
kubectl get endpointslices
```

If there are no endpoints, check whether the Service selector matches the Pod labels.

## Test DNS

From another Pod:

```bash
kubectl exec -it <pod-name> -- nslookup <service-name>
```

## Check Network Policies

```bash
kubectl get networkpolicy
```

## Check CNI Pods

```bash
kubectl get pods -n kube-system
```

Look for networking components such as Calico, Cilium, or another CNI implementation.
