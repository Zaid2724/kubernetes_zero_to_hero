# ☸️ Kubernetes Zero to Hero

> Practical Kubernetes notes covering fundamentals, architecture, workloads, networking, storage, security, Helm, cloud Kubernetes, troubleshooting, and interview preparation.

## 1. What is Kubernetes?

Kubernetes is a container orchestration platform used to deploy, manage, scale, and monitor containerized applications.

### Why do we need it?

Docker can run containers, but managing hundreds of containers manually is difficult.

### Kubernetes provides

- Auto-healing
- Auto-scaling
- Load balancing
- Rolling updates
- Service discovery
- Storage management

### Think

- **Docker** → Runs containers
- **Kubernetes** → Manages containers at scale

## 2. Why Kubernetes?

Docker solves the problem of creating and running containers.

But imagine you have:

- 500 containers
- Multiple servers
- High traffic
- Application failures
- Multiple environments
- New application releases

Managing all of this manually becomes difficult.

### Kubernetes provides

| Problem | Kubernetes Solution |
|---|---|
| Container crashes | Self-healing |
| High traffic | Autoscaling |
| Multiple servers | Cluster management |
| New application version | Rolling updates |
| Server failure | Rescheduling |
| Configuration | ConfigMaps / Secrets |
| Service discovery | Services / DNS |
| External traffic | Ingress / Load Balancer |

## 3. Docker vs Kubernetes

> **Interview tip:** This is one of the most common interview questions.

| Docker | Kubernetes |
|---|---|
| Creates and runs containers | Manages containers at scale |
| Runs mainly on a single host | Manages multiple nodes |
| Uses Dockerfile | Uses YAML manifests |
| Docker Compose for multi-container apps | Kubernetes Deployments / Services |
| Limited orchestration | Full container orchestration |
| Container runtime / tooling | Container orchestration platform |
> **Important:** Docker and Kubernetes are not competitors.

### Typical flow

Application Code
↓
Dockerfile
↓
Docker Image
↓
Container Registry
↓
Kubernetes
↓
Pod

## 4. What is Container Orchestration?

Container orchestration means automatically managing containers.

It includes:

- Deployment
- Scaling
- Networking
- Load balancing
- Self-healing
- Updates
- Storage
- Scheduling

### Popular orchestration tools

- Kubernetes
- Docker Swarm
- Apache Mesos

Kubernetes became the dominant platform for large-scale container orchestration.

## 5. What is a Pod?

A Pod is the smallest deployable unit in Kubernetes.

### A Pod can contain

```text
Pod
├── Container 1
└── Container 2
```

Containers inside the same Pod can share:

- Network namespace
- IP address
- Storage volumes

### Usually

1 Pod = 1 Main Application Container

### Example

```yaml
apiVersion: v1
kind: Pod

metadata:
  name: nginx-pod

spec:
  containers:
    - name: nginx
      image: nginx
```

### Create

```bash
kubectl apply -f pod.yaml
```

### Check

```bash
kubectl get pods
```

### Delete

```bash
kubectl delete pod nginx-pod
```

## 6. Deployments

You normally should not create Pods directly in production.

Instead, use a Deployment.

A Deployment manages:

```text
Deployment
     |
ReplicaSet
     |
Pods
```

### Example

```yaml
apiVersion: apps/v1
kind: Deployment

metadata:
  name: nginx-deployment

spec:
  replicas: 3

  selector:
    matchLabels:
      app: nginx

  template:
    metadata:
      labels:
        app: nginx

    spec:
      containers:
        - name: nginx
          image: nginx:latest
```

### Apply

```bash
kubectl apply -f deployment.yaml
```

### Check

kubectl get deployments
kubectl get replicasets
```bash
kubectl get pods
```
## 7. ReplicaSet

A ReplicaSet ensures that the required number of Pods are running.

### Example

Desired Pods = 3

Actual Pods = 2

ReplicaSet creates:

1 New Pod

### Relationship

Deployment
↓
ReplicaSet
↓
Pods

In production, use Deployments rather than managing ReplicaSets directly.

## 8. Scaling

### Manual scaling

```bash
kubectl scale deployment nginx-deployment --replicas=5
```

### Result

### Before

```text
Pod 1
Pod 2
Pod 3
```

### After

```text
Pod 1
Pod 2
Pod 3
```
Pod 4
Pod 5
## 9. Services

Pods are temporary.

A Pod can:

```text
Crash
↓
Deleted
↓
Recreated
↓
New IP Address
```

Therefore, we don't normally connect directly to Pod IP addresses.

We use a Service.

```text
User
  |
Service
  |
+-----+-----+-----+
| Pod | Pod | Pod |
+-----+-----+-----+
```

The Service provides a stable network endpoint.

## 10. Types of Services
ClusterIP

Default Service type.

Used for internal communication.

```text
Frontend Pod
     |
ClusterIP Service
     |
Backend Pods
```

### Example

```yaml
apiVersion: v1
kind: Service

metadata:
  name: backend-service

spec:
  selector:
    app: backend

  ports:
    - port: 80
      targetPort: 8080

  type: ClusterIP
```
NodePort

Exposes the application using a Node's IP and port.

`http://NodeIP:30080`

Range:

`30000–32767`

### Example

type: NodePort
LoadBalancer

Commonly used in cloud environments.

```text
Internet
    |
Cloud Load Balancer
    |
Kubernetes Service
    |
Pods
```

### Example

type: LoadBalancer

## 11. Kubernetes Networking

### Basic rule

Every Pod gets its own IP address.

### Communication

Pod → Pod
Pod → Service
External User → Ingress/LoadBalancer → Service → Pod

### Simplified architecture

```text
Internet
   |
Load Balancer / Ingress
   |
Service
   |
Pods
   |
Container
```
## 12. CNI

### CNI stands for

Container Network Interface

### CNI plugins provide networking for Pods.

### Examples

- Calico
- Cilium
- Flannel
- AWS VPC CNI
- Azure CNI

### CNI handles

- Pod IP allocation
- Pod-to-Pod networking
- Network policies
## 13. DNS in Kubernetes

Kubernetes has internal DNS.

### Example Service

backend-service

### Another Pod can communicate using

backend-service

### Fully qualified

`backend-service.namespace.svc.cluster.local`

## 14. ConfigMaps

ConfigMaps store non-sensitive configuration.

### Examples

- Application URL
- Environment
- Log level
- Database host

### Example

```yaml
apiVersion: v1
kind: ConfigMap

metadata:
  name: app-config

data:
  APP_ENV: production
  LOG_LEVEL: info
```

Use as environment variables or mounted files.

## 15. Secrets

Secrets store sensitive information.

### Examples

- Passwords
- API keys
- Tokens
- Certificates

### Example

```yaml
apiVersion: v1
kind: Secret

metadata:
  name: db-secret

type: Opaque

stringData:
  username: admin
  password: password123
```
### Important Interview Point

Kubernetes Secrets are not automatically encrypted just because they are Secrets.

Base64 encoding is not encryption.

Production environments should configure:

- Encryption at rest
- RBAC
- External secret management

### Examples

- AWS Secrets Manager
- Azure Key Vault
- HashiCorp Vault
## 16. Storage

Containers are ephemeral.

If a container is deleted:

Container Data ❌

Kubernetes provides persistent storage.

### Main components

- PersistentVolume (PV)
- PersistentVolumeClaim (PVC)
- StorageClass

### Architecture

```text
Application
     |
PVC
     |
PV
     |
Actual Storage
```

### Examples

- AWS EBS
- Azure Disk
- NFS
- Ceph
## 17. PersistentVolume

PV represents actual storage.

### Example

100 GB Storage
## 18. PersistentVolumeClaim

PVC is a request for storage.

### Example

Application:
"I need 10 GB."

Kubernetes connects the PVC to suitable storage.

### Example

```yaml
apiVersion: v1
kind: PersistentVolumeClaim

metadata:
  name: app-pvc

spec:
  accessModes:
    - ReadWriteOnce

  resources:
    requests:
      storage: 10Gi
```
## 19. StorageClass

StorageClass enables dynamic provisioning.

Instead of manually creating storage:

```text
Developer creates PVC
↓

StorageClass
↓
Cloud Disk Automatically Created
```
## 20. Namespaces

Namespaces logically separate resources.

### Examples

- `default`
- `kube-system`
- `development`
- `testing`
- `production`

### Commands

```bash
kubectl get pods
``` -n kube-system

### Create

```bash
kubectl create namespace dev
```
## 21. Labels and Selectors

Labels are key-value pairs.

### Example

labels:
app: nginx
environment: production

### Selectors find resources.

### Example

selector:
matchLabels:
app: nginx

Services use selectors to identify Pods.

```text
Service
   |
Selector: app=nginx
   |
Pods with app=nginx
```
## 22. Annotations

Annotations store additional metadata.

Unlike labels, annotations are generally not used for selecting objects.

### Examples

- Load Balancer configuration
- Build information
- Monitoring configuration
## 23. Resource Requests and Limits

Very important in production.

resources:

requests:
cpu: "250m"
memory: "256Mi"

limits:
cpu: "500m"
memory: "512Mi"

Requests

Minimum resources required for scheduling.

### The scheduler considers

CPU
Memory

Limits

Maximum resources a container can consume.

Important:

```text
Memory Limit Exceeded
↓
Container may be OOMKilled
```
## 24. Health Checks

Kubernetes supports:

Liveness Probe
Readiness Probe
Startup Probe
Liveness Probe

### Question

Is the application still alive?

### If it fails

Container Restart
Readiness Probe

### Question

Is the application ready to receive traffic?

### If it fails

Pod removed from Service endpoints
Startup Probe

Used for slow-starting applications.

It prevents Kubernetes from killing the application before it finishes starting.

## 25. Liveness vs Readiness
| Liveness Probe | Readiness Probe |
|---|---|
| Is the application alive? | Can the application receive traffic? |
| Failure may restart the container | Pod is removed from Service endpoints |
| Detects dead applications | Controls traffic routing |
## 26. Autoscaling
Horizontal Pod Autoscaler

HPA increases or decreases the number of Pods.

### Example

```text
CPU High
   ↓
3 Pods
   ↓
HPA
   ↓
6 Pods
```

Command:

```bash
kubectl autoscale deployment app \
--min=2 \
--max=10 \
--cpu-percent=70
```
Vertical Pod Autoscaler

### VPA adjusts

CPU
Memory

for Pods.

Cluster Autoscaler

Adds or removes Nodes.

```text
Not enough Node capacity
        ↓
Cluster Autoscaler
        ↓
New Node Added
```
## 27. Scheduling

The Kubernetes Scheduler decides where Pods run.

### It considers

- Resource requests
- Node availability
- Taints
- Tolerations
- Node affinity
- Pod affinity
- Pod anti-affinity
## 28. Taints and Tolerations

Taints repel Pods.

### Example

Node:
Dedicated for Database

### Taint

NoSchedule

Only Pods with matching toleration can run there.

### Think

Taint = Keep Pods Away
Toleration = Permission to Enter
## 29. Node Affinity

Node Affinity tells Kubernetes:

Run this Pod on Nodes matching specific conditions.

### Example

Only run on SSD Nodes.
## 30. Pod Affinity

Run Pods near each other.

### Example

```text
Application Pod
+
Cache Pod

Run on same Node/Zone
```
## 31. Pod Anti-Affinity

Keep Pods apart.

### Example

```text
Replica 1 → Node 1
Replica 2 → Node 2
Replica 3 → Node 3
```

This improves availability.

## 32. Rolling Updates

Kubernetes can update applications without downtime.

### Example

Version 1
```text
Pod 1
Pod 2
Pod 3
```

    ↓

Version 2

Pod 1 → Updated
Pod 2 → Updated
Pod 3 → Updated

### Commands

```bash
kubectl set image deployment/app \
app=nginx:1.25
```

### Check

```bash
kubectl rollout status deployment/app
```
## 33. Rollback

### Check history

```bash
kubectl rollout history deployment/app
```

### Rollback

```bash
kubectl rollout undo deployment/app
```
## 34. StatefulSet

Used for stateful applications.

### Examples

- Databases
- Kafka
- Elasticsearch

Unlike Deployments:

Pod Names Are Stable

### Example

mysql-0
mysql-1
mysql-2
## 35. DaemonSet

Ensures one Pod runs on every Node.

### Examples

- Monitoring agents
- Logging agents
- Security agents
- CNI components

### Example

```text
Node 1 → Monitoring Pod
Node 2 → Monitoring Pod
Node 3 → Monitoring Pod
```
