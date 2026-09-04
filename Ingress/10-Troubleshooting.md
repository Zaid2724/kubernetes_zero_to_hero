# Ingress Troubleshooting

## 1. Check Ingress

kubectl get ingress

kubectl describe ingress <ingress-name>

---

## 2. Check Ingress Controller

kubectl get pods -A

Check logs:

kubectl logs <controller-pod> -n <namespace>

---

## 3. Check Service

kubectl get svc

Make sure:

Ingress backend service name is correct.

---

## 4. Check Endpoints

kubectl get endpoints

If no endpoints exist:

Check:

Service Selector
        ↓
Pod Labels

They must match.

---

## 5. Check Pods

kubectl get pods

kubectl describe pod <pod-name>

kubectl logs <pod-name>

---

## Common Problems

### 404 Error

Possible reasons:

- Wrong path
- Wrong host
- Incorrect Ingress rule

### 502 / 503 Error

Possible reasons:

- Service has no endpoints
- Pods are not ready
- Wrong target port

### Ingress Not Working

Check:

1. Ingress Controller installed?
2. Correct ingressClassName?
3. Service exists?
4. Service has endpoints?
5. Pods are healthy?
6. DNS configured correctly?