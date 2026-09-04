# What is Kubernetes Ingress?

Ingress is a Kubernetes API object used to manage
external HTTP and HTTPS traffic to applications.

Basic flow:

Internet
   ↓
Ingress
   ↓
Service
   ↓
Pods

Ingress can route traffic based on:

- Domain name
- URL path
- Hostname

Example:

example.com/app1 → app1-service

example.com/app2 → app2-service
Why do we need it?

Without Ingress:

Internet
   ↓
LoadBalancer
   ↓
Service 1

Internet
   ↓
LoadBalancer
   ↓
Service 2

Internet
   ↓
LoadBalancer
   ↓
Service 3

You may end up creating multiple external load balancers.

With Ingress:

Internet
   ↓
One Load Balancer
   ↓
Ingress Controller
   ↓
+-----------+-----------+
|           |           |
/app1       /app2
↓           ↓
Service 1   Service 2

Ingress provides centralized HTTP/HTTPS routing.