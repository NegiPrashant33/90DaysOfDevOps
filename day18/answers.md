# Day 18 Task: Docker for DevOps Engineers

Let's move forward and dig more on other Docker concepts.

## Docker Compose

- Docker Compose is a tool that was developed to help define and share multi-container applications.
- With Compose, we can create a YAML file to define the services and with a single command, can spin everything up or tear it all down.
- Learn more about docker-compose [visit here](https://tecadmin.net/tutorial/docker/docker-compose/)

## What is YAML?

- YAML is a data serialization language that is often used for writing configuration files. Depending on whom you ask, YAML stands for yet another markup language or YAML ain’t markup language (a recursive acronym), which emphasizes that YAML is for data, not documents.
- YAML is a popular programming language because it is human-readable and easy to understand.
- YAML files use a .yml or .yaml extension.
- Read more about it [here](https://www.redhat.com/en/topics/automation/what-is-yaml)



## Tasks Todo

### Task 1
```yaml
version : "3.9"
services:
web:
    image: nginx:latest
    ports:
    - "80:80"
db:
    image: mysql
    ports:
    - "3306:3306"
    environment:
    - "MYSQL_ROOT_PASSWORD=test@123"
```

1. `version: "3.9"`: This specifies the version of the Docker Compose file format being used.

2. `services`: This section defines the services (containers) that you want to run as part of your application. In this case, you have two services defined: `web` and `db`.

3. `web`: This is the service definition for a container named web.
    image: nginx:latest: This specifies that the container should use the latest version of the official Nginx image from Docker Hub.
    ports: 

    This section defines port mapping between the host machine and the container.
    `- "80:80"`: This maps port 80 from the host machine to port 80 in the container. This means that if you access port 80 on your host machine, it will be forwarded to the Nginx container's port 80, allowing you to access the web server.

3. `db`: This is the service definition for a container named db.
    image: mysql: This specifies that the container should use the official MySQL image from Docker Hub.
    
    `ports`: Similar to the web service, this section defines port mapping.
    `- "3306:3306"`: This maps port 3306 from the host machine to port 3306 in the container. Port 3306 is the default port for MySQL.

    `environment`: This section allows you to set environment variables for the container.
    `-"MYSQL_ROOT_PASSWORD=test@123"`: This sets the environment variable MYSQL_ROOT_PASSWORD to "test@123", which will be used as the root password for the MySQL container.


### Task 2

```bash

# Running container as a non root user
docker run -d --name my_nginx_container -p 80:80 --user prashant nginx

# Adding user to the docker group to give the user root privileges
sudo usermod -aG docker prashant
sudo reboot

# Inspecting the container
docker inspect my_nginx_container

# View containers log output
docker logs my_nginx_container

# Stop the container
docker stop my_nginx_container

# Start the container
docker start my_nginx_container

# Remove the conatiner
docker rm my_nginx_container



```

## How to run Docker commands without sudo?

- Make sure docker is installed and system is updated (This is already been completed as a part of previous tasks):
- `sudo usermod -a -G docker $USER`
- Reboot the machine.

For reference you can watch this [video](https://youtu.be/Tevxhn6Odc8)