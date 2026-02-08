# Docker Compose Patterns & Commands

## 1. Basic Structure of docker-compose.yml

```yaml
version: "3.9"

services:
  web:
    build: .
    ports:
      - "8000:8000"
    volumes:
      - .:/app
    environment:
      - DEBUG=1

  db:
    image: postgres:15
    environment:
      POSTGRES_USER: myuser
      POSTGRES_PASSWORD: mypassword
      POSTGRES_DB: mydb
    volumes:
      - db_data:/var/lib/postgresql/data

volumes:
  db_data:

- `version` → Compose file version
- `services` → Containers to run
- `build` → Build Dockerfile in current directory
- `image` → Pull prebuilt image from Docker Hub
- `ports` → Map host:container ports
- `volumes` → Persist data between container restarts
- `environment` → Set environment variables

```

## 2. Common Docker Compose Commands

```
docker-compose up             # Start all services
docker-compose up -d          # Start in detached mode
docker-compose down           # Stop and remove containers, networks
docker-compose build          # Build or rebuild services
docker-compose restart        # Restart all services
docker-compose logs -f        # View logs in real-time
docker-compose exec web bash  # Enter container shell
docker-compose ps             # List running services
```

## 3. Example: Django + Postgres

```
version: "3.9"

services:
  django:
    build: .
    command: python manage.py runserver 0.0.0.0:8000
    volumes:
      - .:/app
    ports:
      - "8000:8000"
    depends_on:
      - db
    environment:
      - DEBUG=1
      - DATABASE_URL=postgres://myuser:mypassword@db:5432/mydb

  db:
    image: postgres:15
    environment:
      POSTGRES_USER: myuser
      POSTGRES_PASSWORD: mypassword
      POSTGRES_DB: mydb
    volumes:
      - postgres_data:/var/lib/postgresql/data

volumes:
  postgres_data:
```

## 4. Example: FastAPI + Redis

```
version: "3.9"

services:
  app:
    build: .
    ports:
      - "8000:8000"
    depends_on:
      - redis

  redis:
    image: redis:7
    ports:
      - "6379:6379"
```

## 5. Best Practices

```
1. Use `.env` files for sensitive environment variables.
2. Always define volumes for databases to prevent data loss.
3. Use specific image tags instead of `latest` for stability.
4. Leverage networks for inter-service communication.
5. Avoid building large images in Compose; build separately for production.
6. Use `depends_on` wisely; it only controls startup order, not readiness.
7. Use `docker-compose.override.yml` for local development overrides.
8. For production, consider using Docker Swarm or Kubernetes instead of Compose.

```

## 6. Notes & Tips

```
- `docker-compose up -d --build` → Rebuild and start services in detached mode.
- `docker-compose exec <service> <command>` → Run command inside container.
- `docker-compose logs -f <service>` → Tail logs for a single service.
- Use named volumes for persistent data between container restarts.
- Compose simplifies multi-container development and local testing.

```
