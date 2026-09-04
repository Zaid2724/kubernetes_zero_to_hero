# Init Containers

Init Containers run before the main application containers start.

```text
Pod Created
     ↓
Init Container 1
     ↓
Init Container 2
     ↓
Main Application Starts
```

The main container does not start until all Init Containers complete successfully.

## Use Cases

* Wait for a database
* Download configuration
* Create required files
* Perform initialization
* Run pre-start tasks

## Example

```yaml
apiVersion: v1
kind: Pod

metadata:
  name: init-demo

spec:

  initContainers:
    - name: init-container
      image: busybox
      command:
        - sh
        - -c
        - "echo Initializing application"

  containers:
    - name: nginx
      image: nginx
```

## Init Container vs Main Container

| Init Container             | Main Container            |
| -------------------------- | ------------------------- |
| Runs first                 | Runs after init completes |
| Must complete successfully | Runs application          |
| Runs sequentially          | Can run continuously      |

## Important Point

If an Init Container fails:

```text
Main Application ❌ Does Not Start
```

Check:

```bash
kubectl describe pod <pod-name>
kubectl logs <pod-name> -c <init-container-name>
```