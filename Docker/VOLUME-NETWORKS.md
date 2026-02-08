# Docker Volumes & Networks

Understanding **volumes and networks** is crucial for **data persistence, container communication, and isolation**.

---

## 1. Types of Volumes

### a) Named Volumes

```bash
docker volume create mydata
docker run -v mydata:/app/data myimage
```

```text
- Managed by Docker
- Persist data even if container is removed
- Best for databases or important data in production
```

### b) Bind Mounts

```bash
docker run -v $(pwd)/data:/app/data myimage
```

```text
- Maps a host directory into the container
- Useful for development
- Changes on host reflect inside container immediately
```

### c) Anonymous Volumes

```bash
docker run -v /app/data myimage
```

```text
- Docker assigns a random name
- Data persists until container is removed
- Less control, rarely used in production
```

## 2. Managing Volumes

```bash
docker volume ls           # List all volumes
docker volume inspect mydata   # Inspect volume details
docker volume rm mydata        # Remove a specific volume
docker volume prune             # Remove all unused volumes
```

## 3. Networks in Docker

### a) Default Networks

```text
- bridge: Default for standalone containers
- host: Container shares host network
- none: No network
```

### b) User-Defined Bridge Networks

```bash
docker network create mynetwork
docker run --network mynetwork --name db postgres
docker run --network mynetwork --name web myapp
```

```text
- Allows containers to communicate by name
- Provides better isolation than default bridge
```

### c) Overlay Networks(for Sworm)

```text
- Used in Docker Swarm or multi-host setups
- Enables services across multiple hosts to communicate
```

## 4. Using Networks in Compose

```yaml
version: "3.9"

services:
  web:
    build: .
    networks:
      - mynet

  db:
    image: postgres
    networks:
      - mynet

networks:
  mynet:
```

```
- Compose automatically creates networks for services
- Use service names as hostnames
```

## 5. Volumes in Compose

```yaml
version: "3.9"

services:
  db:
    image: postgres
    volumes:
      - db_data:/var/lib/postgresql/data

volumes:
  db_data:
```

```
- Named volumes ensure data persists across container restarts
- Bind mounts can be used for local development
```

## 6. Best Practices

```
1. Use named volumes for databases and critical data in production.
2. Use bind mounts for development to reflect code changes immediately.
3. Always inspect volumes if data is missing or unexpected behavior occurs.
4. Use custom bridge networks for container isolation and communication.
5. Avoid using the host network in production unless necessary.
6. Prune unused volumes and networks to save disk space.
7. For multi-host setups, use overlay networks or orchestration tools.
```
