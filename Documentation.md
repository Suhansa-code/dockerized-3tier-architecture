# Documentation

## 1. Setup Instructions

### Prerequisites
- Docker and Docker Compose installed.
- A code editor (e.g., Visual Studio Code).
- Internet access to pull base images.

### Steps to Build, Run, and Stop Containers

1. **Clone the Repository**:
   ```bash
   git clone <repository-link>
   cd <repository-directory>```
   
2. **Build and Run Containers**

Run the following command to build and start all services:

```bash
docker-compose up --build
```


* This will:
Build Docker images for the frontend and backend.
Pull the MongoDB image for the database.
Start all services and connect them to the appropriate networks.

3. **Access the Application**:

Frontend: Visit http://localhost:80 in your browser.
Backend: Test API endpoints on http://localhost:3000.
Database: MongoDB is accessible on localhost:27017.

4. **Stop Containers**:

Stop running containers gracefully:
```bash
Copy code
docker-compose down
```

This will also remove any temporary containers and networks created during the session.


## 2. Network and Security Configurations

### Network Configurations
- The `docker-compose.yml` defines two networks:
  - **`frontend_network`**: Used for communication between the frontend and backend.
  - **`backend_network`**: Used for communication between the backend and database.

### Ports
- **Frontend**: Exposed on port `80` (mapped to container port `80`).
- **Backend**: Exposed on port `3000` (mapped to container port `3000`).
- **Database**: Exposed on port `27017` (mapped to container port `27017`).

### Security Settings
- Database credentials are set via the `MONGO_URI` environment variable in the backend service.


## 3. Troubleshooting Guide

### Common Issues and Solutions

1. **Containers Fail to Start**:
   - Ensure Docker and Docker Compose are installed and running.
   - Check for typos or syntax errors in the `docker-compose.yml` file.

2. **Frontend Not Accessible**:
   - Verify that the frontend service is running using the following command:
     ```bash
     docker ps
     ```
   - Make sure port `80` is not already in use on your host machine.

3. **Backend API Not Responding**:
   - Check the backend service logs for errors:
     ```bash
     docker-compose logs backend
     ```
   - Confirm that the `MONGO_URI` environment variable is correctly configured in the backend service.

4. **Database Connection Issues**:
   - Verify the database service is running:
     ```bash
     docker ps
     ```
   - Ensure the backend can resolve the database hostname (`database`) in the Docker network.

5. **Rebuild Containers After Changes**:
   - If changes are made to Dockerfiles or the application code, rebuild the containers:
     ```bash
     docker-compose up --build
     ```

6. **General Debugging**:
   - Use Docker Compose logs to troubleshoot issues across all services:
     ```bash
     docker-compose logs
     ```

