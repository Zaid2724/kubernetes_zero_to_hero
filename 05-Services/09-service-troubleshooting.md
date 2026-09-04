# Service Troubleshooting

The most common Service problem is simple:

> The Service selector does not match the Pod labels.

## Step 1: Check the Service

```bash
kubectl get svc
kubectl describe svc <service-name>
```

Check:

* Selector
* Ports
* Service type

## Step 2: Check Pods

```bash
kubectl get pods --show-labels
```

Verify that Pod labels match the Service selector.

Example:

```text
Service selector:
app=nginx

Pod label:
app=nginx
```

## Step 3: Check Endpoints

```bash
kubectl get endpoints
```

Or:

```bash
kubectl get endpointslices
```

If no backend endpoints exist, check:

```text
Service Selector
        ↓
Pod Labels
```

## Step 4: Check Pod Health

```bash
kubectl get pods
kubectl describe pod <pod-name>
```

Check whether Pods are Ready.

## Common Problems

### No Endpoints

Possible causes:

* Incorrect selector
* Incorrect Pod labels
* Pods are not Ready

### Connection Refused

Possible causes:

* Wrong `targetPort`
* Application not listening on the expected port
* Container configuration issue

### Service Not Accessible Externally

Check:

* Service type
* NodePort
* LoadBalancer status
* Ingress configuration
* Firewall or security rules
