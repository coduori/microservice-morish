YOLO APP 

 Overview
 Spin up the services :

 docker compose up

 This will build and launch all required containers.

 Architecture

 The docker-compose.yml file defines:

Three Services:
 1 yolo-app-frontend
 2 yolo-app-backend
 3 mongo - MongoDB database

Persistent storage - mounted volume
Named Volume:app-mongo-data -Ensure MongoDB data persists.

Bridge network
Custom network : yolo-net -bridge network to allow inter container communication


Frontend: yolo-app-front-end 

This  container that spins up the front end where end users can view the app. 
The service is exposed on port 3000

Dockerfile Directives 

FROM : base image used
WORKDIR: working directory inside the container
COPY: Copy files form the host machine to the container
RUN: Used to execute commands like "npm install"
EXPOSE: opens the port that the container listens on, in this case port 3000
CMD: Defines the command to run when the container starts ["npm", "start"]


Backend: yolo-app-backend

Contains the backend logic
runs on port 5000. 

Dockerfile Directives 

Database: Mongo
It persists data via the mounted volume app-mongo-data and listens on the default Mongo port 27017.
