
## Services

### MongoDB

- **Image**: `mongo`
- **Volume**: `data:/data/db`
- **Env File**: `./env/mongo.env`

### Backend

- **Build Context**: `./backend`
- **Port**: `80:80`
- **Volumes**:
  - `logs:/app/logs`
  - `./backend:/app`
  - `/app/node_modules`
- **Env File**: `./env/backend.env`
- **Depends On**: `mongodb`

### Frontend

- **Build Context**: `./frontend`
- **Port**: `3000:3000`
- **Volume**: `./frontend:/app/src`
- **Env File**: `./env/frontend.env`
- **Depends On**: `backend`
- **Options**: `stdin_open: true`, `tty: true`

## Setup

1. Clone the repository
2. Create `.env` files in `env/` directory
3. Run `docker-compose up --build`
4. Access:
   - Backend: `http://localhost:80`
   - Frontend: `http://localhost:3000`

## Stopping Containers

- `Ctrl+C` in the terminal running `docker-compose up`
- `docker-compose down`

## Additional Commands

- Logs: `docker-compose logs`
- Restart Service: `docker-compose restart <service_name>`
- Prune: `docker system prune`

## Troubleshooting

- Check service logs: `docker-compose logs`
- Verify environment variables in `.env` files

## Documentation

Refer to the official Docker documentation or contact the project maintainers for further assistance.
# Here's a README file to explain the procedures for your Docker project

Docker Project
This project sets up a multi-container Docker application with MongoDB, a backend service, and a frontend service using Docker Compose.

Prerequisites
Docker installed on your machine
Docker Compose installed on your machine
Project Structure

.
├── docker-compose.yml
├── backend
│ ├── Dockerfile
│ └── ... (other backend files)
├── frontend
│ ├── Dockerfile
│ └── ... (other frontend files)
└── env
├── mongo.env
├── backend.env
└── frontend.env
Docker Compose File
The docker-compose.yml file defines the following services:

mongodb: MongoDB database service
backend: Backend application service
frontend: Frontend application service
Services
MongoDB Service
Image: mongo
Volumes:
data:/data/db
Environment Variables: ./env/mongo.env
Backend Service
Build Context: ./backend
Ports: 80:80
Volumes:
logs:/app/logs
./backend:/app
/app/node_modules
Environment Variables: ./env/backend.env
Depends On: mongodb
Frontend Service
Build Context: ./frontend
Ports: 3000:3000
Volumes:
./frontend:/app/src
Environment Variables: ./env/frontend.env
Depends On: backend
Additional Options:
stdin_open: true
tty: true
Volumes
data
logs
Setup
Step 1: Clone the Repository
Clone this repository to your local machine:

sh
Copy code
git clone <repository_url>
cd <repository_directory>
Step 2: Create Environment Files
Create the necessary environment files in the env directory. You need three files:

mongo.env
backend.env
frontend.env
Populate these files with the required environment variables for each service.

Step 3: Build and Start the Containers
Use Docker Compose to build and start all the services:

sh
Copy code
docker-compose up --build
This command will:

Build the backend and frontend services using their respective Dockerfiles.
Start the MongoDB, backend, and frontend services.
Set up the specified volumes for data persistence and log storage.
Step 4: Access the Services
Backend: Accessible at <http://localhost:80>
Frontend: Accessible at <http://localhost:3000>
Step 5: Stop the Containers
To stop the running containers, press Ctrl+C in the terminal where docker-compose up is running. Alternatively, you can stop the containers with:

sh
Copy code
docker-compose down
This command will stop and remove all the containers defined in the docker-compose.yml file.

Additional Commands
To view logs: docker-compose logs
To restart services: docker-compose restart <service_name>
To remove all stopped containers and unused networks: docker system prune
Troubleshooting
If you encounter any issues, check the logs of the services for errors:

sh
Copy code
docker-compose logs
Ensure that all environment variables are correctly set in their respective .env files.

Conclusion
This README provides an overview of setting up and running a multi-container Docker application using Docker Compose. If you have any questions or need further assistance, please refer to the official Docker documentation or contact the project maintainers.
