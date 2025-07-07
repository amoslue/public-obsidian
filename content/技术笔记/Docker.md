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

### Mapping the port
docker run ==-p host:container== xxx
![[Pasted image 20250707193545.png]]
### Mapping Volume
docker run ==-v folderpath== xxx
![[Pasted image 20250707193807.png]]
### Commands
=== image ===
docker build -t name:tag .         # Build image from Dockerfile
docker images                      # List local images
docker rmi image_name              # Remove image
docker pull image_name             # Download image from Docker Hub
docker save -o file.tar image_name # Save image to tar file
docker load -i file.tar            # Load image from tar file

=== container ===
docker run image_name                      # Run container
docker run -it image_name /bin/bash        # Run with interactive terminal
docker run -d -p 80:80 image_name          # Detached mode, port mapping
docker run -e VAR=value image_name         # Set env variable
docker ps                                  # List running containers
docker ps -a                               # List all containers
docker stop container_id                   # Stop container
docker start container_id                  # Start container
docker rm container_id                     # Remove container
docker exec -it container_id bash          # Run command in running container

==== volume ====
docker volume create volume_name           # Create volume
docker run -v volume_name:/path image_name # Mount volume
docker run -v $(pwd):/app image_name       # Bind mount current dir

==== compose ===
docker-compose up                         # Start all services
docker-compose down                       # Stop and remove all
docker-compose build                      # Build images
