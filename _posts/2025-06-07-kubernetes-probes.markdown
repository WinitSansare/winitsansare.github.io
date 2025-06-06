---
layout: post
title: "Understanding Kubernetes Probes"
date: 2025-06-07 22:00:00 +0000
categories: devops
---
Kubernetes provides several health check mechanisms called **probes**. They help the control plane determine if your application is running correctly and is ready to receive traffic.

## Types of Probes

- **Liveness Probe**: Detects if a container is running. If the probe fails repeatedly, Kubernetes restarts the container.
- **Readiness Probe**: Indicates when a container is ready to accept traffic. Failed readiness checks remove the pod from service load balancers until the probe succeeds again.
- **Startup Probe**: Allows slow-starting applications extra time to become ready before liveness probes begin.

## Example Configuration

```yaml
livenessProbe:
  httpGet:
    path: /healthz
    port: 8080
  initialDelaySeconds: 10
  periodSeconds: 5
readinessProbe:
  httpGet:
    path: /ready
    port: 8080
  initialDelaySeconds: 5
  periodSeconds: 5
```

Using probes ensures Kubernetes can react to failures quickly and route traffic only to healthy pods, improving reliability for your services.
