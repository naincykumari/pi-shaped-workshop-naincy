## Core Concept Questions

**1. Why is Docker useful in building and deploying microservices?**  
Docker provides consistent environments, lightweight isolation, and fast deployment. Microservices benefit from Docker because each service can run in its own container with all dependencies bundled, reducing conflicts and improving scalability.

**2. What is the difference between a Docker image and a container?**  
A Docker image is a blueprint or template. A container is a running instance of that image. For scaling, multiple containers can be spawned from the same image, enabling consistent replication of the application.

**3. How does Kubernetes complement Docker when running at scale?**  
Kubernetes automates deployment, scaling, and management of containerized applications. It provides features like load balancing, service discovery, and self-healing, making it ideal for running hundreds of Docker containers in production.
