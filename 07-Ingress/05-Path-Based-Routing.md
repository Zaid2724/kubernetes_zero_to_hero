# Path-Based Routing

Ingress can route traffic based on URL paths.

Example:

example.com/users
      ↓
users-service


example.com/products
      ↓
products-service

Example YAML:

apiVersion: networking.k8s.io/v1
kind: Ingress

metadata:
  name: app-ingress

spec:
  ingressClassName: nginx

  rules:
  - host: example.com

    http:
      paths:

      - path: /users
        pathType: Prefix

        backend:
          service:
            name: users-service
            port:
              number: 80

      - path: /products
        pathType: Prefix

        backend:
          service:
            name: products-service
            port:
              number: 80

Traffic flow:

example.com/users
        ↓
Ingress Controller
        ↓
users-service
        ↓
Users Pods