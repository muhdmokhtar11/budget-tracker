# Personal Budget Tracker

A JHipster-based personal budget tracking application with a modern web interface.

## 🚀 Quick Start for Team Members

### Prerequisites

- [Docker Desktop](https://www.docker.com/products/docker-desktop/) installed and running
- [Git](https://git-scm.com/) installed

### Getting Started

1. **Clone the repository**:
   ```bash
   git clone <your-repo-url>
   cd personal-budget-tracker
   ```

2. **Run the application**:
   ```bash
   docker-compose up -d
   ```

3. **Access the application**:
   - **Web application**: http://localhost:8080
   - **API documentation**: http://localhost:8080/swagger-ui/index.html
   - **Database**: localhost:3306 (MySQL)

### Useful Commands

- **Start the application**: `docker-compose up -d`
- **Stop the application**: `docker-compose down`
- **View logs**: `docker-compose logs -f`
- **View logs for specific service**: `docker-compose logs -f app`
- **Restart a service**: `docker-compose restart app`
- **Remove everything (including data)**: `docker-compose down -v`
- **Rebuild the application**: `docker-compose up -d --build`

## 🛠️ Development

### Running in Development Mode

For development without Docker:

1. **Start the database only**:
   ```bash
   docker-compose up mysql -d
   ```

2. **Run the backend**:
   ```bash
   ./mvnw spring-boot:run
   ```

3. **In another terminal, start the frontend**:
   ```bash
   npm start
   ```

### Building the Application

- **Build JAR**: `./mvnw clean package`
- **Build Docker image**: `npm run java:docker`
- **Run tests**: `./mvnw test`

## 📁 Project Structure

- `src/main/java/` - Backend Java code
- `src/main/webapp/` - Frontend React application
- `src/main/resources/` - Configuration files
- `docker-compose.yml` - Docker Compose configuration
- `src/main/docker/` - Docker-related files

## 🔧 Configuration

The application uses the following default configuration:
- **Port**: 8080
- **Database**: MySQL 9.2.0
- **Environment**: Production mode
- **JVM Memory**: 512MB max, 256MB initial

## 🐛 Troubleshooting

### Port Already in Use
```bash
# Check what's using the port
lsof -i :8080

# Kill the process or change the port in docker-compose.yml
```

### Database Connection Issues
```bash
# Check if MySQL is running
docker-compose ps

# Check MySQL logs
docker-compose logs mysql

# Restart the services
docker-compose restart
```

### Out of Disk Space
```bash
# Clean up Docker resources
docker system prune -a --volumes
```

## 📚 Additional Documentation

For more detailed information, see [DOCKER_SETUP.md](DOCKER_SETUP.md).

