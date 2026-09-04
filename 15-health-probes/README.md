# Kubernetes Health Probes

Kubernetes uses probes to check the health and availability of applications.

There are three important probes.

## Startup Probe

Checks whether the application has started successfully.

Useful for slow-starting applications.

```text
Application Starting
        ↓
Startup Probe
        ↓
Application Started
```

## Liveness Probe

Checks whether the application is still alive.

If it repeatedly fails:

```text
Liveness Probe Fails
        ↓
Container Restarted
```

## Readiness Probe

Checks whether the application is ready to receive traffic.

```text
Pod Starts
   ↓
Readiness Probe
   ↓
Ready
   ↓
Added to Service endpoints
```

If the readiness probe fails, the Pod is normally removed from ready Service endpoints but is not necessarily restarted.

## Simple Difference

```text
Startup
→ Has the application started?

Liveness
→ Is the application alive?

Readiness
→ Can the application receive traffic?
```

## Interview Answer

> Startup probes check application startup, liveness probes determine whether a container should be restarted, and readiness probes determine whether a Pod should receive Service traffic.
