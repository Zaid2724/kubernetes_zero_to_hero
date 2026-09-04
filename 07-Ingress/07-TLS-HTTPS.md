# HTTPS / TLS with Ingress

Ingress can terminate SSL/TLS connections.

Traffic:

User
  ↓ HTTPS
Ingress Controller
  ↓ HTTP or HTTPS
Service
  ↓
Pod

TLS certificate is usually stored as a Kubernetes Secret.

Example:

kubectl create secret tls app-tls \
--cert=certificate.crt \
--key=private.key

Ingress:

spec:

  tls:
  - hosts:
    - example.com

    secretName: app-tls

The Ingress Controller uses the certificate
to handle HTTPS traffic.