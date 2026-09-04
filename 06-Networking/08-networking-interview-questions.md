# Kubernetes Networking Interview Questions

## 1. How do Pods communicate with each other?

Pods communicate through the Kubernetes network. Each Pod has its own IP address, and Pods should be able to communicate across Nodes.

---

## 2. Can containers inside the same Pod communicate using localhost?

Yes. Containers inside the same Pod share the network namespace.

---

## 3. Why should applications not depend on Pod IP addresses?

Pod IP addresses can change when Pods are recreated.

Use a Service for stable communication.

---

## 4. What is CNI?

CNI is the standard interface used to configure container networking. CNI plugins provide the actual Pod networking implementation.

---

## 5. What is kube-proxy?

kube-proxy is a Kubernetes component involved in implementing Service networking and forwarding traffic to backend Pods.

---

## 6. What is CoreDNS?

CoreDNS provides DNS and service discovery inside the Kubernetes cluster.

---

## 7. What is a NetworkPolicy?

A NetworkPolicy controls allowed ingress and egress traffic for Pods.

---

## 8. How do you troubleshoot a Service that is not working?

Check:

```text
Service
  ↓
Selector
  ↓
Pod Labels
  ↓
Endpoints / EndpointSlices
  ↓
Pod Readiness
  ↓
DNS
  ↓
NetworkPolicy
```

---

## 9. Explain the complete traffic flow to an application.

```text
External User
      ↓
Ingress / LoadBalancer
      ↓
Service
      ↓
Pod
      ↓
Container
```
