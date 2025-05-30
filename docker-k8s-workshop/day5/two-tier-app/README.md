# Day 5 - Two-Tier Helm App

### Core Concept Questions

#### 1. Why are liveness and readiness probes critical in keeping a product’s user experience stable and reliable?
**Liveness probes** detect if a pod is stuck and needs to be restarted, ensuring the app doesn’t remain in a broken state.  
**Readiness probes** ensure traffic is only sent to pods that are fully initialized, preventing user errors during startup or crash recovery.

#### 2. How does HPA help in handling flash sales, seasonal load spikes, or traffic surges in real-world applications like an e-commerce platform?
HPA dynamically adjusts the number of pods based on CPU or memory usage. This ensures that during flash sales or spikes in traffic, the app auto-scales to meet demand, maintaining availability and performance.

### Optimization Strategies

- Set `requests` and `limits` to right-size resources for cost efficiency.
- Used lightweight images (`nginx`, `http-echo`) to reduce startup time and memory usage.
- Added probes to ensure traffic only reaches healthy containers.
- Enabled HPA to autoscale and save resources during idle times.
