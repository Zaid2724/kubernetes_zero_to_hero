# Managed Kubernetes

Cloud providers offer managed Kubernetes services.

The main ones are:

```text
AWS
→ EKS

Microsoft Azure
→ AKS

Google Cloud
→ GKE
```

## What Does Managed Kubernetes Mean?

The cloud provider manages important Kubernetes infrastructure components, especially the control plane.

You are mainly responsible for:

```text
Applications
Pods
Deployments
Services
Configuration
Access management
Networking
Worker Nodes / Compute configuration
```

The exact responsibility depends on the service and chosen operating mode.

---

# EKS

Amazon Elastic Kubernetes Service.

Common integrations:

```text
EKS
├── IAM
├── VPC
├── EC2
├── EBS
├── Load Balancers
└── CloudWatch
```

Basic architecture:

```text
AWS
 ↓
EKS Control Plane
 ↓
Worker Nodes / Compute
 ↓
Pods
```

---

# AKS

Azure Kubernetes Service.

Common integrations:

```text
AKS
├── Azure AD / Entra ID
├── Virtual Network
├── Azure Load Balancer
├── Azure Disks
└── Azure Monitor
```

---

# GKE

Google Kubernetes Engine.

Common integrations:

```text
GKE
├── IAM
├── VPC
├── Load Balancing
├── Persistent Disk
└── Cloud Monitoring
```

## Simple Comparison

| Service | Cloud Provider  |
| ------- | --------------- |
| EKS     | AWS             |
| AKS     | Microsoft Azure |
| GKE     | Google Cloud    |

## Important Interview Question

### What is the difference between self-managed and managed Kubernetes?

```text
Self-Managed Kubernetes
→ You manage the control plane and infrastructure.

Managed Kubernetes
→ Cloud provider manages major control-plane infrastructure, while you manage workloads and configuration.
```

## Interview Answer

> EKS, AKS, and GKE are managed Kubernetes services provided by AWS, Azure, and Google Cloud. They reduce the operational overhead of managing Kubernetes infrastructure and integrate with their respective cloud services.
