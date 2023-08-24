## Docker Important interview Questions.

1. What is the difference between Image, Container and Engine ?

    **Image** is a lightweight, standalone, executable package of software that includes everything needed to run an application: code, runtime, system tools, system libraries and settings.

    An image is a read-only template with instructions for creating a Docker container. Often, an image is based on another image, with some additional customization.

    A **Container** is a standard unit of software that packages up code and all its dependencies so the application runs quickly and reliably from one computing environment to another.

    A container is a running instance of an image.

    A Container is a bundle of Application, Application libraries required to run your application and the minimum system dependencies.


    **Docker Engine** is the core component of docker that allows you to build, run and manage containers. It has two main components.

    - docker d (docker daemon)
    - docker cli (docker command line interface)

    Docker CLI (Command Line Interface) to issue commands, the Docker Daemon (dockerd) interprets and executes those commands to manage containers, images, networks, and other Docker-related operations.

    (When you use the Docker CLI to issue commands, you're essentially sending Docker API requests to the Docker Daemon. The Docker CLI translates your human-readable commands into API requests that the Docker Daemon can understand and execute.) 

2. What is the difference between COPY and ADD command used in Dockerfile ?

    **COPY**

    The `COPY` command is used to copy files or directories from the host machine's filesystem into the image. It's a straightforward operation and only deals with local files. It doesn't have any special processing for URLs or tar extraction.


    `COPY src/ /app/`

    **ADD**

    The `ADD` command has similar functionality to COPY, but it has additional features. In addition to copying local files, ADD command also supports two other sources. 
    
    - A URL instead of a local file/directory.
    - Extract tar from the source directory into the destination 


    `ADD http://example.com/sample.txt /app`

    `ADD app.tar.gz /app/`

3. What is the difference between RUN and CMD command used in Dockerfile ?

    **RUN**

    The `RUN` command is used to execute commands at build time. These commands are run in the shell of the image's underlying operating system, and their purpose is to install packages, set up dependencies, and perform other tasks required to prepare the image for running applications.

    **CMD**

    The `CMD` command is used to provide the default command that should be executed when a container based on the image is run. This is the command that defines what the container should run as its main process when started.


4. How will you reduce the size of the docker image ?

    Following are the ways in which we can reduce our docker image size
    
    - Using a minimal/distroless base image
    - Minimizing the number of layers in an Image 
    - Using Multi-Stage builds
    - Copying only necessary files and directories

    Check out this [Reduce Docker Image Size](https://devopscube.com/reduce-docker-image-size/) blog for an detailed explanation on how to reduce the size of the docker image.

5. Why and when to use Docker ?

6. Explain the Docker components and how they interact with each other.

    Docker components
    
    - **docker daemon**: The Docker daemon (dockerd) listens for Docker API requests and manages Docker objects such as images, containers, networks, and volumes. A daemon can also communicate with other daemons to manage Docker services.

    - **docker client**: The Docker client (docker) is the primary way that many Docker users interact with Docker. When you use commands such as docker run, the client sends these commands to dockerd, which carries them out. The docker command uses the Docker API. The Docker client can communicate with more than one daemon.

    - **docker image**: A Docker image is a lightweight, standalone, executable package of software that includes everything needed to run an application: code, runtime, system tools, system libraries and settings.

    - **docker container**: A container is a standard unit of software that packages up code and all its dependencies so the application runs quickly and reliably from one computing environment to another.

    - **docker registry**: A Docker registry stores Docker images. Docker Hub is a public registry that anyone can use, and Docker is configured to look for images on Docker Hub by default.

    - **docker compose**: Docker Compose is a tool for defining and running multi-container applications using a single configuration file (usually a docker-compose.yml file). 

    - **docker swarm**: Docker Swarm is a container orchestration tool. Container orchestration refers to the process of managing and automating the deployment, scaling, and operation of multiple containers within a cluster or environment.

    ![docker architecture](/day21/images/217507877-212d3a60-143a-4a1d-ab79-4bb615cb4622.png)


    From a `Dockerfile` a `Docker Image` is build and this image is used to run `Docker container`. Docker container is basically the running instance of a Docker Image.

    Now to do this we run Docker commands, Docker commands are run using `Docker Client` (Docker command line interface), using Docker client we input human readable commands which are then converted to `Docker API` request, the API Request is accepted and executed by `Docker Daemon`. So basically we run docker commands using docker cli which are instructions given to docker daemon that executes those instructions.

    `Docker Registry` is where we store our docker images and `Docker compose` is used to run multi-container applications using a single configuration file.

    This is how docker components are related to each other.


7. Explain the terminology

    - **Docker file**: Dockerfile is a configuration file which consist of instructions to build a Docker image. It is a blueprint for a docker image

    - **Docker image**: A Docker image is a lightweight, standalone, executable package of software that includes everything needed to run an application: code, runtime, system tools, system libraries and settings.

    - **Docker container**: A container is a standard unit of software that packages up code and all its dependencies so the application runs quickly and reliably from one computing environment to another. Container is an running instance of an image.

    - **Docker compose**: Docker Compose is a tool for defining and running multi-container applications using a single configuration file (usually a docker-compose.yml file). 

8. In what real scenario you have used Docker ?

9. Docker vs Hypervisor

10. What are the advantages and disadvantages of using docker ?

11. What is a docker namespace ?

12. What is a docker registry ?


13. What is ENTRYPOINT command used in Dockerfile ?

    **ENTRYPOINT**
    
    The `ENTRYPOINT` instruction is similar to `CMD`, but it provides more control and flexibility. It specifies the command that should be the entry point for the container. The difference is that the arguments passed to ENTRYPOINT are fixed, and any additional arguments provided when running the container will be treated as arguments to the ENTRYPOINT command. This allows you to create more dynamic and consistent behavior for containers.
