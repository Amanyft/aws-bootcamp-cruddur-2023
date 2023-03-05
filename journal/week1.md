# Week 1 — App Containerization
*Docker extension installation in VScode .<br>

![Docker](https://user-images.githubusercontent.com/80603078/222934496-69d32b26-07e2-4e87-9a11-82a25ffd422d.PNG)

<br>
*The creation of the Dockerfile for the backend app built on top of the python:3.10-slim-buster docker image <br>

![docker2](https://user-images.githubusercontent.com/80603078/222934783-0511c86f-d84d-4a20-a1a8-966a6ebd36d6.PNG)

  <br>

  *The creation of the Dockerfile for the frontend app built on top of the node:16.18 docker image <br>
  
  ![docker3](https://user-images.githubusercontent.com/80603078/222934595-46f1f4bc-6979-4d11-8ce8-96c854a2a1e1.PNG)
  <br>
  *The different elements of a dockerfile structure :<br> 
     <b> FROM </b> Base Image  : A Dockerfile starts with a base image, which is the foundation of the new Docker image . It contains a pre-built and pre-configured operating system with all its dependencies, libraries, and software packages needed to run that image .<br>
     <b> ENV </b> Environment Variables : The ENV command is used to set environment variables within the Docker image.<br>
     <b> COPY </b> <Source> <Destination> : used to copy files or directories from the host machine (where Docker is running) into the Docker image being built.<br>
     <b> WORKDIR </b> : used to set the working directory for subsequent instructions.<br>
  *learnt about the difference between Container Os and Host OS , copied data from and to both of them .<br>
  *built a docker image for the frontend app and backend app seperately then used Docker compose file to build both of the app containers at the same time . <br>
  *learnt about Docker container security best practices :<br>
           -managed(ECS,EKS) vs unmanaged(outside cloud) container services .<br>
           -Docker architecture(components): docker client , docker server ,Docker registry , Docker container, docker image .<br>

