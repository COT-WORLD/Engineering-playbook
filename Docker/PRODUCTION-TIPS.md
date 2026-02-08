# Docker Production Tips & Best Practices

Running Docker in production requires careful planning for **security, stability, logging, and resource management**. This guide covers key practices for production-ready Docker setups.

---

## 1. Use Minimal Base Images

```text
- Prefer slim or alpine images to reduce attack surface and image size.
- Examples:
  - python:3.11-slim
  - node:18-alpine
  - nginx:alpine
```

## 2. Runs as Non-Root User

```
# Example Dockerfile snippet
FROM python:3.11-slim

# Create a user
RUN useradd -ms /bin/bash appuser
USER appuser

WORKDIR /app
COPY . .
CMD ["python", "app.py"]
```

```
- Avoid running containers as root to improve security.
- Some base images already provide non-root users (e.g., nginx:alpine).
```

## 3. Set Resource Limits

```
# Example docker-compose resource limits
services:
  web:
    build: .
    deploy:
      resources:
        limits:
          cpus: "0.5"
          memory: "512M"
```

```
- Limit CPU and memory to prevent a single container from exhausting host resources.
- Especially important in multi-container production environments.
```

## 4. Logging & Monitoring

```
- Use centralized logging:
  - docker logs → Basic logs per container
  - Consider logging drivers: json-file (default), syslog, fluentd, awslogs
- Example:
  docker run --log-driver=syslog <image>

- Monitor container health:
  - Use `HEALTHCHECK` in Dockerfile
  - Use tools like Prometheus, Grafana, or cAdvisor
```

## 5. Version and tags

```
- Always pin specific versions, do not use 'latest' in production.
- Example:
  FROM python:3.11.5-slim
- Tag images with meaningful versions:
  docker build -t myapp:1.0.0 .

```

## 6. Secure Secrets & Environment Variables

```
- Never store passwords or API keys in Dockerfile.
- Use environment variables or secrets management:
  - Docker secrets (for Swarm/Kubernetes)
  - .env files (development only)
- Example in Compose:
  environment:
    DATABASE_PASSWORD: ${DB_PASSWORD}
```

## 7. Minimize Layers & Keep Images Lightweight

```
RUN apt-get update && apt-get install -y \
    curl \
    vim \
 && rm -rf /var/lib/apt/lists/*
```

```
- Combine multiple commands into a single RUN to reduce image layers.
- Remove caches and unnecessary files to reduce image size.
```

## 8. Health Checks

```
# Example Dockerfile HEALTHCHECK
HEALTHCHECK --interval=30s --timeout=5s --retries=3 \
  CMD curl -f http://localhost:8000/health || exit 1
```

```
- Allows orchestration tools (Docker Swarm, Kubernetes) to detect unhealthy containers.
```

## 9. Network & Port Management

```
- Use custom bridge networks for container isolation.
- Avoid exposing unnecessary ports to the public.
- Example: only expose 443 for web traffic in production.
```

## 10. Image Scanning and Updates

```
- Scan images for vulnerabilities using tools like:
  - docker scan <image>
  - Trivy
- Regularly update base images and dependencies to patch security issues.
```
