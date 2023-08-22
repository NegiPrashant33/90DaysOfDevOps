# Docker for DevOps Engineers

## Docker-Volume

Docker allows you to create something called volumes. Volumes are like separate storage areas that can be accessed by containers. They allow you to store data, like a database, outside the container, so it doesn't get deleted when the container is deleted.
You can also mount from the same volume and create more containers having same data.
[reference](https://docs.docker.com/storage/volumes/)

## Docker Network

Docker allows you to create virtual spaces called networks, where you can connect multiple containers (small packages that hold all the necessary files for a specific application to run) together. This way, the containers can communicate with each other and with the host machine (the computer on which the Docker is installed).
When we run a container, it has its own storage space that is only accessible by that specific container. If we want to share that storage space with other containers, we can't do that. [reference](https://docs.docker.com/network/)


## Task 1 


```YAML

version : "3.3"
services:
  web:
    image: varsha0108/local_django:latest
    deploy:
        replicas: 2
    ports:
      - "8001-8005:8001"
    volumes:
      - my_django_volume:/app
  db:
    image: mysql
    ports:
      - "3306:3306"
    environment:
      - "MYSQL_ROOT_PASSWORD=test@123"
volumes:
  my_django_volume:
    external: true
   
```

```shell

# start multi container application in detached mode
docker-compose up -d

# Scale the "web" service to 3 replicas
docker-compose scale web=3  

# View the status of all containers
docker-compose ps

# To view the logs of a specific service
docker-compose logs web

# stop and remove all containers, networks, and volumes associated with the application
docker-compose down

``


## Task 2

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

FROM python:3

WORKDIR /app

RUN pip install django==3.2

COPY . /app

RUN python [manage.py](http://manage.py/) migrate

EXPOSE 8000

CMD ["python","[manage.py](http://manage.py/)","runserver","0.0.0.0:8000"]
```

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

As you enter the container you will notice that all the contents of your current directory are copied to the container in the **/app** directory as instructed in the docker file

We have also created a test.log file inside the container to show the importance of having a volume associated with the container in order to backup data.


As we kill the container and then again create a new one, you can notice that the file we created test.log before is no longer available. To resolve this issue and persist our data we will use the concept of **Volume**.


Use http://localhost:8000/ url to run the application on your browser


### Creating a Volume


```bash
docker volume create --name django_todo_volume --opt type=none --opt device=/home/prashant/docker/volumes/django-todo --opt o=bind
```


- **name= <docker volume name>:** flag is used to give docker volume name
- **opt:** flag is used to give additional options for the volume we create
- **type= none:** specifies the volume type, our volume is not of any specific type.
- **device= <path>:** specifies the path on the host system where the volume's data will be stored
- **o=bind:** configures the volume to be a bind mount. A bind mount allows you to mount a directory from the host system into the container, effectively sharing the content between the host and the container.

```bash
# To inspect the docker volume

docker volume inspect <volume name>
```

Now we will attach our container with the volume we have created


Before doing that we have to kill our container, as the volume is attached with container while we create the container.

```bash
# To kill a container

docker kill <container id>
```


Attaching a volume to the container

```bash
docker run -d -p 8000:8000 --mount source=<volume name>,target=<work directory of container> <docker image name>
```

- **d:** flag specifies to run the container in detached mode, that is the container will run in backgroung
- **p:** flag allows us to map the port of the host system to the port in the container. This allows you to access services running in the container via port 8000 on the host.
- **mount:** flag is used to mount a volume into the container
- **source:** specifies the name of the volume you want to mount
- **target:** directory path inside the container where the volume will be mounted, it is the working directory of the container

Now we have all the contents of the container backed up in our **/docker/volume/django-todo** directory


So now if we create any new file/directory inside our container, that file/directory will also be reflected back in our volume thereby backing up our data.


**Docker commands**

- List all docker volume

    `docker volume ls`

- Create a new volume

    `docker volume create --name django-app-volume --opt type=none --opt device=<path> --opt o=bind`

- Mount(attach) the docker volume to the docker container

    `docker run -d --mount source=<volume name>,target=<container's working directory> -p 8000:8000 django-app:latest`

- Inspect a volume

    `docker volume inspect <volume name>`