The biggest mistake with Deployments is memorizing YAML without understanding the relationship:

Deployment → ReplicaSet → Pods

A Deployment does not directly manage containers. It manages ReplicaSets, which maintain Pods.

Most important commands
# Create or update
kubectl apply -f deployment.yaml

# Check deployments
kubectl get deployments

# Check Pods
kubectl get pods

# Scale
kubectl scale deployment <name> --replicas=5

# Update image
kubectl set image deployment/<name> <container>=<image>:<tag>

# Check rollout
kubectl rollout status deployment/<name>

# View history
kubectl rollout history deployment/<name>

# Rollback
kubectl rollout undo deployment/<name>

# Troubleshoot
kubectl describe deployment <name>

Remember this
Pod
↓
Runs your container

ReplicaSet
↓
Maintains the number of Pods

Deployment
↓
Manages ReplicaSets and application updates