# Personal Budget Tracker - Docker Setup

This guide will help you run the Personal Budget Tracker application using Docker.

## Prerequisites

- Docker Desktop installed and running
- Docker Compose (usually comes with Docker Desktop)

## Quick Start

1. **Clone the repository** (if you haven't already):

   ```bash
   git clone <your-repo-url>
   cd personal-budget-tracker
   ```

2. **Run the application**:

   ```bash
   docker-compose up -d
   ```

3. **Access the application**:
   - Web application: http://localhost:8080
   - API documentation: http://localhost:8080/swagger-ui/index.html
   - Database: localhost:3306 (MySQL)

## Alternative: Build from Source

If you want to build the Docker image locally instead of pulling from Docker Hub:

1. **Build the image**:

   ```bash
   npm run java:docker
   ```

2. **Update the docker-compose.yml** to use the local image:

   ```yaml
   app:
     image: personalbudgettracker:latest
   ```

3. **Run the application**:
   ```bash
   docker-compose up -d
   ```

## Useful Commands

- **Start the application**: `docker-compose up -d`
- **Stop the application**: `docker-compose down`
- **View logs**: `docker-compose logs -f`
- **View logs for specific service**: `docker-compose logs -f app`
- **Restart a service**: `docker-compose restart app`
- **Remove everything (including data)**: `docker-compose down -v`

## Development Mode

For development, you can run the application without Docker:

1. **Start the database only**:

   ```bash
   docker-compose up mysql -d
   ```

2. **Run the application locally**:

   ```bash
   ./mvnw spring-boot:run
   ```

3. **In another terminal, start the frontend**:
   ```bash
   npm start
   ```

## Troubleshooting

### Port Already in Use

If you get a port conflict error:

```bash
# Check what's using the port
lsof -i :8080

# Kill the process or change the port in docker-compose.yml
```

### Database Connection Issues

If the app can't connect to the database:

```bash
# Check if MySQL is running
docker-compose ps

# Check MySQL logs
docker-compose logs mysql

# Restart the services
docker-compose restart
```

### Out of Disk Space

If you encounter disk space issues:

```bash
# Clean up Docker resources
docker system prune -a --volumes
```

## Environment Variables

You can customize the application by setting environment variables in the `docker-compose.yml` file:

- `SPRING_PROFILES_ACTIVE`: Set to `dev` for development mode
- `_JAVA_OPTIONS`: Adjust JVM memory settings
- `MYSQL_DATABASE`: Change the database name

## Team Sharing Options

### Option 1: Docker Hub (Recommended)

1. Push the image to Docker Hub
2. Share the `docker-compose.yml` file
3. Team members pull and run

### Option 2: Private Registry

1. Set up a private Docker registry
2. Push images there
3. Team members pull from private registry

### Option 3: Image Export/Import

1. Export the image: `docker save personalbudgettracker > app.tar`
2. Share the tar file
3. Team members import: `docker load < app.tar`

### Option 4: Source Code Only

1. Share the source code
2. Team members build locally using `npm run java:docker`
3. Run with `docker-compose up -d`
