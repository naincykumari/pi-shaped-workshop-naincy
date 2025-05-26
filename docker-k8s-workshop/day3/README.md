# Kubernetes Networking Setup - Hello World API

## How would you expose an internal microservice (e.g., user-auth) differently than a public-facing frontend?
Internal microservices like user-auth are usually exposed using ClusterIP or headless services, restricting access to within the cluster only. This protects sensitive services from external exposure.

Public-facing frontends are exposed using Ingress or LoadBalancer services, allowing controlled access via domain names, TLS, and routing rules.

## Why might a product use Ingress instead of directly exposing each microservice via LoadBalancer?
Efficiency: One LoadBalancer per microservice is costly and wasteful. Ingress consolidates multiple routes behind a single IP.

Path-based Routing: Ingress supports routing traffic to different services using paths/domains.

TLS Termination: Ingress can handle HTTPS termination centrally.

Centralized Configuration: Easier to manage rules, auth, rate limiting, etc., via annotations.



## Services

Two services are configured:

- **ClusterIP** (`hello-world-clusterip`): Internal access only
- **NodePort** (`hello-world-nodeport`): Access externally on Minikube IP + NodePort (30036)

## Ingress

An Ingress named `hello-world-ingress` is set up using the Minikube Ingress addon.  
It exposes the app on path-based routing:

- **Host**: `hello-world.local`
- **Path**: `/hello` → forwards to `hello-world-clusterip` on port 81

Enable Ingress Addon: 

$ minikube addons enable ingress

Update `/etc/hosts`:

$ echo "$(minikube ip) hello-world.local" | sudo tee -a /etc/hosts

### Access Table

| Access Type  | URL                                | Expected Response        |
|--------------|------------------------------------|--------------------------|
| NodePort     | http://<minikube-ip>:30036         | JSON message from API    |
| Ingress      | http://hello-world.local/hello     | JSON message from API    |
| PortForward  | http://localhost:8081              | JSON message from API    |
 
