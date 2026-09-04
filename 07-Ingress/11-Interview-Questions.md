# Kubernetes Ingress Interview Questions

## 1. What is Ingress?

Ingress is a Kubernetes API resource that manages
HTTP and HTTPS routing from external users to
Services inside a Kubernetes cluster.

---

## 2. What is an Ingress Controller?

An Ingress Controller is the component responsible
for implementing Ingress rules and routing traffic
to Kubernetes Services.

---

## 3. Difference between Ingress and Ingress Controller?

Ingress:
Defines routing rules.

Ingress Controller:
Reads and implements those routing rules.

---

## 4. Can Ingress work without an Ingress Controller?

No.

Ingress only defines the desired routing configuration.

An Ingress Controller is required to process
and apply those rules.

---

## 5. Difference between Ingress and LoadBalancer?

LoadBalancer exposes a Service externally.

Ingress provides Layer 7 HTTP/HTTPS routing and
can route multiple applications using hosts or paths.

---

## 6. Explain the traffic flow.

User
↓
DNS
↓
Load Balancer
↓
Ingress Controller
↓
Service
↓
Pod

---

## 7. What are the main types of Ingress routing?

- Path-based routing
- Host-based routing

---

## 8. What happens if the Service has no endpoints?

The Ingress Controller cannot forward traffic
to application Pods.

The user may receive a 502 or 503 error depending
on the controller and configuration.

---

## 9. How do you troubleshoot Ingress?

1. Check Ingress rules.
2. Check Ingress Controller.
3. Check Service.
4. Check Endpoints.
5. Check Pod health.
6. Check DNS.
7. Check controller logs.

---

## 10. What is ingressClassName?

It tells Kubernetes which Ingress Controller
should handle the Ingress resource.