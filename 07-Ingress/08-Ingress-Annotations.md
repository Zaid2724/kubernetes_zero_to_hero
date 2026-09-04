# Ingress Annotations

Annotations provide additional configuration
to the Ingress Controller.

Examples:

- SSL redirect
- URL rewrite
- Authentication
- Rate limiting
- Timeouts

Example:

metadata:
  annotations:
    nginx.ingress.kubernetes.io/ssl-redirect: "true"

Important:

Annotations are often controller-specific.

For example:

NGINX annotations may not work with
AWS Load Balancer Controller.