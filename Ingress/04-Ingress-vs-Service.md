# Ingress vs Service

| Ingress | Service |
|---|---|
| HTTP/HTTPS routing | Exposes Pods |
| Works at Layer 7 | Mainly network access abstraction |
| Routes by host/path | Routes traffic to Pod endpoints |
| Requires Controller | Built-in Kubernetes resource |
| Usually external traffic | Internal or external access |

Example:

Internet
   ↓
Ingress
   ↓
Service
   ↓
Pods
Easy way to remember
Ingress = Traffic Router

Service = Stable Network Endpoint

Pod = Application