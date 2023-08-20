# Docker Project for DevOps Engineers.

## Dockerfile

Docker is a tool that makes it easy to run applications in containers. Containers are like small packages that hold everything an application needs to run. To create these containers, developers use something called a Dockerfile.

A Dockerfile is like a set of instructions for making a container. It tells Docker what base image to use, what commands to run, and what files to include. For example, if you were making a container for a website, the Dockerfile might tell Docker to use an official web server image, copy the files for your website into the container, and start the web server when the container starts.

For more about Dockerfile visit [here](https://rushikesh-mashidkar.hashnode.dev/dockerfile-docker-compose-swarm-and-volumes)


## Task Todo

### Creating a Dockerfile

Clone the github repository https://github.com/LondheShubham153/django-todo-cicd/tree/develop

```bash
# Clone the repository
git clone https://github.com/LondheShubham153/django-todo-cicd/tree/develop
```

Make the following changes to the Dockerfile, from this docker file we will build an image, then we will create a container and execute the container as well.

**Note**: You may encounter a problem while creating the container as I did, only half of the files of my current directory were getting copied to the container /app directory, this is because we have a .dockerignore file in the repository and as the name suggest of the file, the file or directory name mentioned in the .dockerignore file will not get copied to the container, to resolve this issue remove the files/directories mentioned in the .dockerignore file.

```bash
vim .dockerignore
```

```bash
vim Dockerfile
```

```bash
# Dockerfile

# Use the official Python 3 base image
FROM python:3

# Set the working directory inside the container to /app
WORKDIR /app

# Install Django 3.2 using pip
RUN pip install django==3.2

# Copy the contents of the current directory into the /app directory in the container
COPY . /app

# Run Django migrations to set up the database schema
RUN python manage.py migrate

# Expose port 8000 to the outside world (for incoming traffic)
EXPOSE 8000

# Define the command that will be executed when the container starts
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]
```

### Building the image and running the container

```bash
# Build an image, make sure you are in the same directory 
# where your docker file is present

docker build . -t django-todo-app

# To check the docker image
docker images

# Create a container from the image
docker run -d -p 8000:8000 django-todo-app:latest

# Execute the container
docker exec -it <container id> bash
```


![]()


![]()

### Verify that the application is working

Use http://localhost:8000/ url to run the application on your browser
![Application Running on browser](/day17/images/Screenshot%20from%202023-08-11%2021-34-46.png)



### Push the image to docker repository

```bash

# login to dockerhub and enter your credentials
docker login

# The image name should be of the following convention to push it to docker hub
<docker hub user name>/<image name>

# To change the image name
docker image tag <old image name> <new image name>

docker push <image name>

```

![Docker hub](/day17/images/Screenshot%20from%202023-08-18%2020-24-11.png)