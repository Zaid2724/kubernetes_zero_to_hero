# Kubernetes Service Interview Questions

## 1. What is a Kubernetes Service?

A Service provides a stable network endpoint and DNS name to access one or more Pods.

---

## 2. Why do we need a Service?

Pod IP addresses can change when Pods are recreated. A Service provides stable access to the application.

---

## 3. How does a Service find Pods?

Using labels and selectors.

```text
Service Selector
       ↓
Matching Pod Labels
```

---

## 4. What is ClusterIP?

The default Service type used for internal communication within the Kubernetes cluster.

---

## 5. What is NodePort?

A Service type that exposes an application using a Node IP address and a port.

Example:

```text
NodeIP:30080
```

---

## 6. What is LoadBalancer?

A Service type used to expose an application externally through an infrastructure or cloud-provider load balancer.

---

## 7. Difference between `port` and `targetPort`?

```text
port
↓
Service port

targetPort
↓
Container/Pod port
```

Example:

```text
Client → Service:80 → Pod:8080
```

---

## 8. What happens if a Pod is deleted?

The Service remains available.

If the Pod is managed by a Deployment, a replacement Pod is created and becomes part of the Service when it matches the selector and is ready.

---

## 9. What is Service Discovery?

Service discovery allows applications to find other applications using stable Service names instead of Pod IP addresses.

Example:

```text
backend-service
```

---

## 10. What do you check when a Service has no endpoints?

Check:

```text
1. Service selector
2. Pod labels
3. Pod status
4. Pod readiness
5. Namespace
```
