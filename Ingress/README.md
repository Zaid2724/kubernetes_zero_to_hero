# Kubernetes Ingress and Ingress Controller

This folder covers:

- What is Ingress?
- What is an Ingress Controller?
- Why do we need Ingress?
- How traffic flows
- Ingress vs Service
- Path-based routing
- Host-based routing
- TLS/HTTPS
- Annotations
- NGINX Ingress Controller
- Troubleshooting
- Interview Questions

The one architecture diagram you should remember
                    Internet
                       │
                       ▼
                      DNS
                       │
                       ▼
               Cloud Load Balancer
                       │
                       ▼
              Ingress Controller
                       │
             ┌─────────┴─────────┐
             │                   │
             ▼                   ▼
       users-service        api-service
             │                   │
             ▼                   ▼
         Users Pods           API Pods
         
The shortest possible explanation
Ingress
= Defines routing rules.

Ingress Controller
= Reads those rules and routes traffic.

Service
= Sends traffic to Pods.

Pod
= Runs the application.