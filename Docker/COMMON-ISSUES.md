# Docker Common Issues & Fixes

This guide covers **frequent Docker problems** encountered in development and production, along with **solutions**.

---

## 1. Port Already in Use

```text
Error:
  bind: address already in use
```

### Fix

```text
# Find which process is using the port
lsof -i :8000   # Linux/macOS
netstat -ano | findstr :8000  # Windows

# Kill the process
kill <pid>       # Linux/macOS
taskkill /PID <pid> /F  # Windows
```

```text
- Ensure host ports are free before running containers.
```

## 2. Docker Daemon Not Running

```text
Error:
  Cannot connect to the Docker daemon
```

### Fix

```text
# Linux
sudo systemctl start docker
sudo systemctl enable docker

# macOS
- Make sure Docker Desktop is running
```

```text
- On Windows, start Docker Desktop as Administrator.
```

## 3. Permission Denied on Volumes

```text
Error:
  permission denied while accessing mounted volume
```

### Fix

```text
# Adjust ownership/permissions
sudo chown -R $USER:$USER ./your_folder
sudo chmod -R 755 ./your_folder

# Run container as user (recommended)
docker run -u $(id -u):$(id -g) -v $(pwd):/app <image>
```

```text
- Ensure container user has access to host-mounted directories.
```

## 4. Container Exits Immediately

```text
Error:
  Container stops right after starting
```

### Fix

```text
- Check the CMD or ENTRYPOINT in Dockerfile.
- Run container interactively to debug:
  docker run -it <image> /bin/bash
- Ensure the main process does not exit immediately.
```

## 5. Docker Build Cache Issues

```text
Problem:
  Changes not reflecting after docker build
```

### Fix

```text
- Docker caches layers; use --no-cache when making dependency changes.
```

```text
- Docker caches layers; use --no-cache when making dependency changes.
```

## 6. Network Issues Between Containers

```text
Problem:
  Containers cannot communicate
```

### Fix

```text
# Use the same user-defined network
docker network create mynetwork
docker run --network mynetwork --name db postgres
docker run --network mynetwork --name web myapp
```

```text
- Docker Compose automatically handles networking.
- Use service names as hostnames in Compose.
```

## 7. Volume Not Persisting Data

```text
Problem:
  Container data lost after restart
```

### Fix

```yaml
# Use named volumes in docker-compose.yml
volumes:
  mydata:

services:
  db:
    image: postgres
    volumes:
      - mydata:/var/lib/postgresql/data
```

```
- Bind mounts are useful for development, named volumes for production.
```

## 8. Docker Image Too Large

```
Problem:
  Image size is unnecessarily large
```

### Fix

```
# Use slim or alpine base images
FROM python:3.11-slim

# Combine RUN commands to reduce layers
RUN apt-get update && apt-get install -y curl vim \
 && rm -rf /var/lib/apt/lists/*
# Use multi-stage builds to copy only artifacts
```

## 9. General Cleanup Commands

```
# Remove stopped containers
docker container prune

# Remove unused images
docker image prune

# Remove unused volumes
docker volume prune

# Remove everything unused
docker system prune -a
```
