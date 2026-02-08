# Dockerfile Patterns & Best Practices

## 1. Basic Dockerfile Structure

```dockerfile
# Base image
FROM python:3.11-slim

# Set working directory
WORKDIR /app

# Copy dependency file
COPY requirements.txt .

# Install dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Copy application code
COPY . .

# Default command
CMD ["python", "app.py"]
```

## 2. Key Instructions

```
FROM       → Base image for your container
WORKDIR    → Set working directory inside container
COPY / ADD → Copy files/folders into container
RUN        → Execute commands during build
CMD        → Default command for container execution
ENTRYPOINT → Fixed command that can take additional arguments
ENV        → Set environment variables
EXPOSE     → Declare container port (documentation only)
USER       → Switch to non-root user

```

## 3. Multi-Stage Builds (Reduce Image Size)

```
# Build stage
FROM node:18 as build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# Production stage
FROM nginx:alpine
COPY --from=build /app/dist /usr/share/nginx/html

- Build the application in one stage
- Copy only the final build artifacts to a minimal image
- Results in smaller and more secure production images
```

## 4. Python/Django Example

```
FROM python:3.11-slim

WORKDIR /app

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

# Avoid Python buffering for real-time logs
ENV PYTHONUNBUFFERED=1

# Expose Django default port
EXPOSE 8000

# Run using Gunicorn
CMD ["gunicorn", "myapp.wsgi:application", "--bind", "0.0.0.0:8000"]
```

## 5. Node.js/React Example

```
# Build stage
FROM node:18 as build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# Serve stage
FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]

```

## 6. Misc / System Cleanup

```
1. Use minimal base images (e.g., slim, alpine) to reduce image size.
2. Combine RUN commands to reduce layers:

   RUN apt-get update && apt-get install -y \
       curl \
       vim \
    && rm -rf /var/lib/apt/lists/*

3. Use a .dockerignore file to avoid copying unnecessary files.
4. Set environment variables instead of hardcoding values.
5. Run as a non-root user in production for security.
6. Pin versions of dependencies to prevent unexpected updates.
7. Use multi-stage builds to keep images lightweight.
8. Leverage Docker build cache by copying dependencies first, then application code.
```
