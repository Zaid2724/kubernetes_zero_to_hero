# Deploying an Application in Production

A production Kubernetes application should not be just:

```text
Deployment + Service
```

A basic production setup usually looks like:

```text
Internet
    ↓
Ingress / LoadBalancer
    ↓
Service
    ↓
Deployment
    ↓
Multiple Pods
```

Additional components:

```text
ConfigMap
→ Application configuration

Secret
→ Passwords and sensitive values

Readiness Probe
→ Controls traffic

Liveness Probe
→ Restarts unhealthy containers

Requests and Limits
→ Resource management

HPA
→ Automatic Pod scaling

PVC
→ Persistent storage when required

NetworkPolicy
→ Traffic restrictions
```

## Typical Application Structure

```text
production-app/
│
├── deployment.yaml
├── service.yaml
├── ingress.yaml
├── configmap.yaml
├── secret.yaml
└── hpa.yaml
```

## Production Checklist

```text
☐ Multiple replicas
☐ Resource requests and limits
☐ Readiness probe
☐ Liveness probe
☐ ConfigMap
☐ Secret
☐ Service
☐ Ingress or LoadBalancer
☐ Autoscaling
☐ Monitoring and logging
☐ Network security
```

## Important Concept

```text
Deployment
→ Runs the application

Service
→ Stable access

Ingress
→ External HTTP/HTTPS routing

Probes
→ Health management

HPA
→ Scaling

ConfigMap / Secret
→ Configuration management
```

## Interview Answer

> For a production Kubernetes deployment, I would use multiple replicas, proper resource requests and limits, health probes, externalized configuration, secure secrets management, Services, controlled external access, autoscaling, monitoring, logging, and appropriate network security.
