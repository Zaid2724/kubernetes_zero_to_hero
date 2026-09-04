Complete traffic flow:

User
  ↓
DNS
  ↓
Load Balancer
  ↓
Ingress Controller
  ↓
Ingress Rules
  ↓
Kubernetes Service
  ↓
Pod
  ↓
Container
Step-by-Step

User accesses:

https://example.com/app

DNS resolves the domain.
Traffic reaches the Load Balancer.
Load Balancer sends traffic to the Ingress Controller.
Ingress Controller checks the Ingress rules.

It finds:

/app → app-service

Traffic goes to the Service.
Service forwards traffic to a healthy Pod.