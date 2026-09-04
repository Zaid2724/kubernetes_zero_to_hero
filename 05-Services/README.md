The biggest mistake beginners make is thinking Pods can be accessed directly using their IP addresses. Pod IPs are temporary and can change when Pods are recreated.

That is why Kubernetes uses Services.

Deployment
    ↓
Pods (dynamic IPs)
    ↑
Service (stable endpoint)
    ↑
Users / Other Applications

What you need to remember
Pod        → Runs the application

ReplicaSet → Maintains the number of Pods

Deployment → Manages application deployment and updates

Service    → Provides stable access to Pods