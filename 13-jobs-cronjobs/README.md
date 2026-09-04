# Kubernetes Jobs and CronJobs

## Job

A **Job** runs a task until it completes successfully.

Example:

```text
Run database migration
        ↓
Task completes
        ↓
Job finishes
```

Unlike a Deployment, a Job is not designed to run forever.

## Example

```yaml
apiVersion: batch/v1
kind: Job

metadata:
  name: database-job

spec:
  template:
    spec:
      containers:
        - name: job
          image: busybox
          command: ["echo", "Hello Kubernetes"]

      restartPolicy: Never
```

---

# CronJob

A **CronJob** creates Jobs on a schedule.

Example:

```text
Every day at 2 AM
        ↓
CronJob
        ↓
Job created
        ↓
Task runs
```

Example use cases:

* Database backups
* Scheduled reports
* Cleanup tasks

## Example

```yaml
apiVersion: batch/v1
kind: CronJob

metadata:
  name: backup-job

spec:
  schedule: "0 2 * * *"

  jobTemplate:
    spec:
      template:
        spec:
          containers:
            - name: backup
              image: busybox
              command: ["echo", "Backup started"]

          restartPolicy: OnFailure
```

## Commands

```bash
kubectl get jobs
kubectl get cronjobs
```

## Interview Answer

> A Job runs a task until completion, while a CronJob creates Jobs based on a defined schedule.
