# Host-Based Routing

Ingress can route traffic based on domain names.

Example:

app.example.com
       ↓
app-service


api.example.com
       ↓
api-service

Example:

spec:
  ingressClassName: nginx

  rules:

  - host: app.example.com

    http:
      paths:
      - path: /
        pathType: Prefix

        backend:
          service:
            name: app-service
            port:
              number: 80


  - host: api.example.com

    http:
      paths:
      - path: /
        pathType: Prefix

        backend:
          service:
            name: api-service
            port:
              number: 80