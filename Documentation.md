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
   cd <repository-directory>'''
2. **Build and Run Containers**

Run the following command to build and start all services:

```bash
docker-compose up --build'''


* This will:
Build Docker images for the frontend and backend.
Pull the MongoDB image for the database.
Start all services and connect them to the appropriate networks.
Access the Application:

Frontend: Visit http://localhost:80 in your browser.
Backend: Test API endpoints on http://localhost:3000.
Database: MongoDB is accessible on localhost:27017 (use a database client if needed).
Stop Containers:

Stop running containers gracefully:
bash
Copy code
docker-compose down
This will also remove any temporary containers and networks created during the session.
2. Network and Security Configurations
Network Configurations:

The docker-compose.yml defines two networks:
frontend_network: Used for communication between the frontend and backend.
backend_network: Used for communication between the backend and database.
Ports:

Frontend: Exposed on port 80 (mapped to container port 80).
Backend: Exposed on port 3000 (mapped to container port 3000).
Database: Exposed on port 27017 (mapped to container port 27017).
Security Settings:

Database credentials are set via the MONGO_URI environment variable in the backend service.
