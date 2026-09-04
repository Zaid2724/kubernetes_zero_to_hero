# Multi-Container Pods

A Pod can contain multiple containers.

Example:

```text
Pod
│
├── Application Container
│
└── Sidecar Container
```

## When should you use multiple containers?

Use multiple containers when they are tightly coupled.

Examples:

* Log collector
* Monitoring agent
* Proxy
* Sidecar
* Configuration helper

## Example Architecture

```text
Pod
│
├── Application
│     └── Runs on port 8080
│
└── Proxy
      └── Runs on port 80
```

Both containers share:

* Network
* IP address
* Volumes

## Communication

Containers can communicate using:

```text
localhost:<port>
```

Example:

```text
App → localhost:8080
Proxy → localhost:8080
```

## Important Rule

Do not put unrelated applications into the same Pod.

Bad:

```text
Pod
├── Java Application
├── MySQL Database
└── Random Application
```

Better:

```text
Pod 1 → Java Application
Pod 2 → Database
Pod 3 → Another Application
```

## Interview Answer

**Why use multi-container Pods?**

> Multi-container Pods are used when containers are tightly coupled and need to share networking, storage, or lifecycle. A common example is an application container with a sidecar for logging or proxy functionality.