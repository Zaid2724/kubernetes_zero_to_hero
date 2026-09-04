# What is an Ingress Controller?

An Ingress resource only contains routing rules.

It does NOT route traffic by itself.

An Ingress Controller is the actual software that
reads Ingress rules and routes traffic.

Flow:

Ingress Resource
      ↓
Ingress Controller reads rules
      ↓
Routes traffic to Services
      ↓
Services send traffic to Pods
Popular Ingress Controllers
NGINX Ingress Controller
Traefik
HAProxy
AWS Load Balancer Controller
Important Interview Answer

Ingress = Routing rules

Ingress Controller = Software that implements those rules