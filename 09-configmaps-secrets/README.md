# ConfigMaps and Secrets

Applications need configuration such as:

```text
Database URL
Application URL
Environment
Username
Password
API Key
```

Do not hardcode these values inside container images.

Kubernetes provides:

```text
ConfigMap → Non-sensitive configuration

Secret → Sensitive configuration
```

---

# ConfigMap

Example:

```yaml
apiVersion: v1
kind: ConfigMap

metadata:
  name: app-config

data:
  APP_ENV: production
  APP_PORT: "8080"
```

Create:

```bash
kubectl apply -f configmap.yaml
```

Use as environment variables:

```yaml
envFrom:
  - configMapRef:
      name: app-config
```

## Commands

```bash
kubectl get configmap
kubectl describe configmap app-config
kubectl delete configmap app-config
```

---

# Secret

Example:

```yaml
apiVersion: v1
kind: Secret

metadata:
  name: db-secret

type: Opaque

stringData:
  username: admin
  password: mypassword
```

Use in a Pod:

```yaml
env:
  - name: DB_USERNAME
    valueFrom:
      secretKeyRef:
        name: db-secret
        key: username
```

## Important Warning

A Kubernetes Secret should not automatically be considered encrypted. Base64 encoding is **not encryption**.

For production, also consider:

* Encryption at rest
* RBAC restrictions
* External secret management

## ConfigMap vs Secret

| ConfigMap                                     | Secret                                        |
| --------------------------------------------- | --------------------------------------------- |
| Non-sensitive data                            | Sensitive data                                |
| App configuration                             | Passwords, tokens, keys                       |
| Can be environment variables or mounted files | Can be environment variables or mounted files |

## Interview Answer

> ConfigMaps store non-sensitive application configuration, while Secrets are designed for sensitive data such as passwords, tokens, and API keys.
