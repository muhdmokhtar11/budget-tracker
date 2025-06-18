# Personal Budget Tracker - Docker Setup

Simple step-by-step guide to run the application with Docker.

## Prerequisites

- Docker installed
- Docker Compose installed

## Step-by-Step Instructions

### Step 1: Build the Docker Image
```bash
npm run java:docker
```

### Step 2: Build and Package the Application
```bash
./mvnw package -Pprod verify jib:dockerBuild
```

### Step 3: Start the Application
```bash
docker-compose -f src/main/docker/app.yml up
```

## Access the Application

- **Application**: http://localhost:8080
- **Default login**: admin / admin

## Stop the Application
```bash
docker-compose -f src/main/docker/app.yml down
```

