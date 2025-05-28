# Hello World API – Helm Chart

This Helm chart packages the Kubernetes manifests for the Hello World API application.

## 🚀 Installation

```bash
helm install hello-app ./hello-world-chart
```


## 🔄 Upgrade

Update the `values.yaml` file (e.g., change image tag or replica count):

```yaml
replicaCount: 3
image:
  tag: day2
```

Then upgrade using:

```bash
helm upgrade hello-app ./hello-world-chart
```


## Core Concept Questions

### ✅ Why is Helm important for managing configuration across different environments in a real-world product (e.g., dev, staging, prod)?

Helm allows you to template your Kubernetes manifests and inject environment-specific values using `values.yaml` files. This enables consistent application deployments with environment-specific configurations (like image tags, replica counts, domain names) without duplicating manifests.

---

### ✅ How does Helm simplify deployment rollback during a production incident?

Helm tracks release history. If a deployment fails or causes an incident, you can use `helm rollback` to revert to a previous working state with a single command, reducing downtime and operational overhead.

---
