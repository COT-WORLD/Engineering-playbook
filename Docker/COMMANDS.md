# Docker CLI Commands Reference

## 1. Docker Version & Info

- `docker --version` → Check Docker version
- `docker info` → Detailed Docker system info
- `docker system info` → Similar system info

---

## 2. Images

### List Images

- `docker images` → List all local images
- `docker image ls` → Alternative command

### Pull & Push Images

- `docker pull <image>` → Download image from Docker Hub
- `docker push <image>` → Upload image to registry

### Build Images

- `docker build -t <image_name>:<tag> .` → Build image from Dockerfile
- `docker build --no-cache -t <image_name>:<tag> .` → Build without cache

### Remove Images

- `docker rmi <image>` → Remove specific image
- `docker image prune` → Remove dangling images
- `docker system prune -a` → Remove all unused images, containers, volumes, networks

---

## 3. Containers

### Create & Run

- `docker run <image>` → Run container
- `docker run -it <image> /bin/bash` → Interactive terminal in container
- `docker run -d -p 8080:80 <image>` → Run container in detached mode, map ports

### List Containers

- `docker ps` → Running containers
- `docker ps -a` → All containers (running + stopped)

### Stop / Start / Restart / Remove

- `docker stop <container>` → Stop container
- `docker start <container>` → Start container
- `docker restart <container>` → Restart container
- `docker rm <container>` → Remove stopped container
- `docker rm -f <container>` → Force remove running container

### Logs & Stats

- `docker logs <container>` → View logs
- `docker logs -f <container>` → Follow logs in real-time
- `docker stats` → Live resource usage
- `docker inspect <container>` → Detailed container info

### Execute Commands in Running Container

- `docker exec -it <container> /bin/bash` → Enter container shell
- `docker exec <container> <command>` → Run command inside container

---

## 4. Networks & Ports

- `docker network ls` → List networks
- `docker network inspect <network>` → Inspect network
- `docker network create <network>` → Create custom network
- `docker port <container>` → Show container port mapping

---

## 5. Volumes & Storage

- `docker volume ls` → List volumes
- `docker volume inspect <volume>` → Inspect volume
- `docker volume create <volume>` → Create volume
- `docker volume rm <volume>` → Remove volume
- Mount volume: `docker run -v <volume_name>:/app/data <image>`

---

## 6. Misc / System Cleanup

- `docker system prune` → Remove unused containers, networks, images
- `docker container prune` → Remove stopped containers
- `docker volume prune` → Remove unused volumes
- `docker network prune` → Remove unused networks
