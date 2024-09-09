Node Docker Project

This project is a Node.js application that demonstrates how to containerize a Node.js app using Docker. It includes Docker Compose files for different environments: a general setup and a development-specific configuration.
Getting Started
To get started with this project, you’ll need to have Docker and Docker Compose installed on your machine. You can download Docker from Docker's official website and Docker Compose from Docker Compose's installation page.

Prerequisites
Docker
Docker Compose
Configuration
Docker Compose Files
docker-compose-backup.yml: This file provides a basic configuration for running the application. It uses bind mounting for the project directory and an anonymous volume to ignore the node_modules folder. Environment variables are defined directly in the file.

docker-compose.dev.yml: This file is specifically for development purposes. It includes build arguments for setting the environment to development, and runs the application with npm run dev. It also uses bind mounting and an anonymous volume for node_modules.

Environment Variables
Create a .env file in the root directory of the project to specify environment variables:

PORT=3000
NODE_ENV=development
You can alternatively specify environment variables directly in the docker-compose files as shown.

Running the Application
General Setup
Build and Run the Docker Container

Use the docker-compose-backup.yml file to build and run the application:
docker-compose -f docker-compose-backup.yml up --build
Access the Application

The application will be accessible at http://localhost:3000.

Stop the Application

To stop the running containers, use:
docker-compose -f docker-compose-backup.yml down
Development Setup
Build and Run in Development Mode

Use the docker-compose.dev.yml file to build and run the application in development mode:

docker-compose -f docker-compose.dev.yml up --build
Access the Application

The application will be accessible at http://localhost:3000 with development-specific configurations.

Stop the Application

To stop the running containers, use:

docker-compose -f docker-compose.dev.yml down
Testing
To run tests inside the Docker container, use the following command:

docker-compose -f docker-compose.dev.yml exec node-app npm test
Ensure that your package.json file includes a test script to run your tests.

Deployment
To deploy the application, you can push the Docker image to a container registry (e.g., Docker Hub, AWS ECR) and pull it in your production environment. Modify the Dockerfile and Docker Compose configuration as needed for your deployment setup.
![image](https://github.com/user-attachments/assets/7d7d28bd-7a93-4f4d-a62d-4ba0e8f34f08)

