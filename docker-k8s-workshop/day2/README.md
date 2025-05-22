# Day 1 Assignment – Kubernetes Deployment

## ✅ Core Concepts

### Why do we set requests and limits for CPU/memory in a production-grade product?

Setting resource **requests** ensures that the Kubernetes scheduler reserves the minimum resources needed for the pod to run reliably.  
**Limits** define the maximum amount of resources the pod can consume. This prevents resource starvation, promotes fair sharing, and ensures cluster stability, especially in production environments.

### When would a product team apply node affinity in Kubernetes?

A product team uses **node affinity** to influence or constrain pod scheduling to specific nodes. Common scenarios include:
- Deploying workloads that require specific hardware (e.g., GPUs).
- Enforcing compliance or isolation requirements (e.g., dev vs prod nodes).
- Co-locating microservices for performance optimization.
- Scheduling apps across zones or regions for redundancy.

---

## ✅ Affinity Rules Applied

This deployment uses:

- **Node Affinity**: `requiredDuringSchedulingIgnoredDuringExecution` to strictly schedule the pod on a node labeled with `kubernetes.io/hostname: node1`.
- **Tolerations**: Accepts nodes tainted with `workload=day1:NoSchedule`, allowing this pod to be scheduled on a special-purpose node.

These settings ensure the app is placed on a targeted node only, while respecting taints for production-grade control.

---

## ✅ Commands Used

```bash
kubectl label nodes <node-name> kubernetes.io/hostname=node1
kubectl taint nodes <node-name> workload=day1:NoSchedule
kubectl apply -f combined-deployment.yaml
kubectl get pods -o wide
