# Week 1 — App Containerization
 <h4> Docker Architecture(components): </h4>
  
![architecture](https://user-images.githubusercontent.com/80603078/222955577-3a3e8ddc-bd55-4b07-909e-585d88c18e75.png)


<h4> Docker extension installation in VScode </h4>

![Docker](https://user-images.githubusercontent.com/80603078/222934496-69d32b26-07e2-4e87-9a11-82a25ffd422d.PNG)

<br>
<h4>The creation of the Dockerfile for the backend app built on top of the python:3.10-slim-buster docker image </h4>

![docker2](https://user-images.githubusercontent.com/80603078/222934783-0511c86f-d84d-4a20-a1a8-966a6ebd36d6.PNG)

  <br>

  <h4>The creation of the Dockerfile for the frontend app built on top of the node:16.18 docker image </h4>
  
  ![docker3](https://user-images.githubusercontent.com/80603078/222934595-46f1f4bc-6979-4d11-8ce8-96c854a2a1e1.PNG)
  <br>
  <h4>The different elements of a dockerfile structure :</h4> 
     <b> FROM </b> Base Image  : A Dockerfile starts with a base image, which is the foundation of the new Docker image . It contains a pre-built and pre-configured operating system with all its dependencies, libraries, and software packages needed to run that image .<br>
     <b> ENV </b> Environment Variables : The ENV command is used to set environment variables within the Docker image.<br>
     <b> COPY  <Source> <Dest> </b>  : used to copy files or directories from the host machine (where Docker is running) into the Docker image being built.<br>
     <b> WORKDIR </b> : used to set the working directory for subsequent instructions.<br>
     <b> RUN </b> : used to execute a command in a new layer on top of the current image and commit the results. <br>
     <b> EXPOSE </b> : used to specify which ports are exposed by the Docker image.<br>
     <b>CMD</b> : used to specify the default command that should be run when a container based on the Docker image is started . <br>
  
  <h4>The difference between Container OS and Host OS </h4>
  
  - A container OS is typically a lightweight, stripped-down version of a full-fledged operating system that includes only the minimum software and services required to run a container. This includes the container runtime, system libraries, and other dependencies needed to run applications in the container.<br>
  - A Host OS is a complete operating system that runs directly on the host machine and provides a wide range of services and capabilities to support a variety of applications. <br>
  
![OS](https://user-images.githubusercontent.com/80603078/222936089-14b500db-377d-4c90-bd2e-00577c9c504f.PNG)


<br>
  <h4> Building a docker image for the Frontend app </h4>
  
  ![docker5](https://user-images.githubusercontent.com/80603078/222954288-889b9edb-7083-4bed-989f-f79f33ee6be6.PNG)

  <h4> Building a docker image for the Backend app  </h4>
  
 ![docker4](https://user-images.githubusercontent.com/80603078/222954185-2e2db784-1ac6-4578-b2b6-56c42281fe1d.PNG)


  <h4> Docker Compose file use to build both of the App containers at the same time . </h4>
 <br>
 ![docker6](https://user-images.githubusercontent.com/80603078/222956258-fca9ae8a-0b5a-4c47-a0b7-7e93fd1d62fa.PNG)
<br>
  <h4> Docker Container security Best practices :</h4>
           <h6> Managed Container Services VS Unmanaged Container Services .</h6>
                Managed Container Services and Unmanaged Container Services are two different approaches to running and managing containerized applications.<br>
                Managed container services are fully managed platforms that provide a turnkey solution for running and managing containers.<br>
                Examples of managed container services include Amazon ECS, Amazon EKS...<br>
           -Unmanaged Container Services: <br>
            Unmanaged container services require you to manage the underlying infrastructure yourself .<br>
            Examples of unmanaged container services include Docker Swarm, Kubernetes on-premises, and OpenShift.<br>
            


