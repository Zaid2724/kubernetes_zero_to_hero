# Labels and Selectors in ReplicaSets

Labels and selectors are critical for ReplicaSets.

## Label

A label is a key-value pair attached to a Kubernetes object.

Example:

```yaml
labels:
  app: nginx
```

## Selector

A selector tells the ReplicaSet which Pods it should manage.

Example:

```yaml
selector:
  matchLabels:
    app: nginx
```

## Relationship

```text
ReplicaSet Selector
        │
        │ app=nginx
        ↓
┌─────────────────┐
│ Pod 1           │
│ app=nginx       │ ← Managed
└─────────────────┘

┌─────────────────┐
│ Pod 2           │
│ app=nginx       │ ← Managed
└─────────────────┘

┌─────────────────┐
│ Pod 3           │
│ app=apache      │ ← Not Managed
└─────────────────┘
```

## Important Rule

These must match:

```yaml
selector:
  matchLabels:
    app: nginx
```

and:

```yaml
template:
  metadata:
    labels:
      app: nginx
```

If they do not match, Kubernetes will reject the ReplicaSet configuration.

## Interview Point

A ReplicaSet manages Pods using **label selectors**, not Pod names.
