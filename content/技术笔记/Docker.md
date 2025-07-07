### Why do you need docker?
- **Ensure consistency** across environments (dev, test, prod).
- **Package applications** with all dependencies in containers.
- **Simplify deployment** and scaling.
- **Isolate services** for microservice architecture.
- **Improve CI/CD** by making builds and tests reproducible.
### What can docker do?
- **Containerize applications** with all dependencies.
- **Isolate environments** to avoid conflicts.
- **Build, ship, and run** applications consistently across systems.
- **Scale services** easily using orchestration tools like Docker Swarm or Kubernetes.
- **Integrate with CI/CD** pipelines for automated testing and deployment.
### What are containers?
Containers are lightweight, standalone, and executable units that package software with everything needed to run it—code, runtime, libraries, and system tools—ensuring it runs consistently across environments. They share the host OS kernel but are isolated from each other.
### Container vs. VM?
![[Pasted image 20250707183442.png]]
![[Pasted image 20250707182458.png]]

### Container vs Image?
A **Docker image** is a **read-only template** that contains:
- The application code
- All necessary dependencies (libraries, tools, config)
- A base OS layer
It serves as a **blueprint** to create one or more **containers**. Images are built using a **Dockerfile**.