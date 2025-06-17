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

   This will:
   - Build the application from source
   - Start MySQL database
   - Start the application
   - Make it available at http://localhost:8080

3. **Access the application**:
   - Web application: http://localhost:8080
   - API documentation: http://localhost:8080/swagger-ui/index.html
   - Database: localhost:3306 (MySQL)

## Building from Source

The application is automatically built from source when you run `docker-compose up -d`. The build process:

1. Uses Maven to compile the Java application
2. Builds the React frontend
3. Creates a production-ready JAR file
4. Packages everything into a Docker image

### Manual Build (if needed)

If you want to build manually:

```bash
# Build the application
npm run java:docker

# Run with docker-compose
docker-compose up -d
```

## Useful Commands

- **Start the application**: `docker-compose up -d`
- **Stop the application**: `docker-compose down`
- **View logs**: `docker-compose logs -f`
- **View logs for specific service**: `docker-compose logs -f app`
- **Restart a service**: `docker-compose restart app`
- **Remove everything (including data)**: `docker-compose down -v`
- **Rebuild the application**: `docker-compose up -d --build`

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

### Build Issues

If the build fails:

```bash
# Clean and rebuild
docker-compose down
docker system prune -f
docker-compose up -d --build
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

## Team Collaboration

### For New Team Members

1. Clone the repository
2. Ensure Docker Desktop is running
3. Run `docker-compose up -d`
4. Access the application at http://localhost:8080

### Sharing Changes

1. Commit your changes to Git
2. Push to the repository
3. Team members pull the latest changes
4. Run `docker-compose up -d --build` to rebuild with changes

### Database Data

- Database data is persisted in a Docker volume
- To reset data: `docker-compose down -v && docker-compose up -d`
- To backup data: `docker exec personal-budget-tracker-mysql-1 mysqldump -u root personalbudgettracker > backup.sql`
