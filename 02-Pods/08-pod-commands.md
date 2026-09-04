# Important Pod Commands

## List Pods

```bash
kubectl get pods
```

## Watch Pods

```bash
kubectl get pods -w
```

## Detailed Information

```bash
kubectl describe pod <pod-name>
```

## View Logs

```bash
kubectl logs <pod-name>
```

## Previous Container Logs

```bash
kubectl logs <pod-name> --previous
```

## Multi-Container Pod Logs

```bash
kubectl logs <pod-name> -c <container-name>
```

## Enter a Container

```bash
kubectl exec -it <pod-name> -- sh
```

## Get Pod IP

```bash
kubectl get pod -o wide
```

## Get Pod YAML

```bash
kubectl get pod <pod-name> -o yaml
```

## Delete Pod

```bash
kubectl delete pod <pod-name>
```

## Force Delete

```bash
kubectl delete pod <pod-name> --grace-period=0 --force
```

Use force deletion carefully. It should not be your first troubleshooting option.
