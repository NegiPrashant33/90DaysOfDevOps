# Docker for DevOps Engineers.

## Docker

Docker is a software platform that allows you to build, test, and deploy applications quickly. Docker packages software into standardized units called containers that have everything the software needs to run including libraries, system tools, code, and runtime. Using Docker, you can quickly deploy and scale applications into any environment and know your code will run.

Below is the script to install docker and add the current user to the docker group.
```shell
#!/bin/bash

#################
# Author: Prashant Negi
# Date: 14 August 2023
#
# Purpose: Install docker and add the current user to the docker group
# Version: V1
################


# sets script in debug mode
set -x

# exit immediately if any command fails
set -e

# To check if the script is executed using root user privileges
# EUID --> Effective user id, the EUID of root user is 0
if [[ $EUID -ne 0 ]]; then
   echo "This script must be run as root"
   exit 1
fi

echo "Updating the system"
apt update

echo "Installing docker"
apt install docker.io -y

# Grant access to your user to run docker commands
usermod -aG docker $USER

echo "Docker is successfully installed and the \
current user has been added to the docker group"

```


## Tasks

1. `docker run hello-world`, If the `hello-world` image is not available locally, then docker checks Docker hub for it's image and downloads it.

    ```shell
    # list all the docker containers
    docker ps

    # list all the docker images
    docker images
    ```

    >Note: A Docker registry stores Docker images. Docker Hub is a public registry that anyone can use, and Docker is configured to look for images on Docker Hub by default. 

2. To view detailed information about a container or image.

    `docker inspect <container id>`

    `docker inspect <image name>:<image tag>`

3. To list the port mappings for a container.

    `docker port <container id>`

4. Resource usage statistics for a single/multiple containers

    `docker stats <container id>`

    `docker stats <container id 1> <container id 2>`

5. To view the processes running inside a container.

    `docker top <container id>`

6. To save an image to a tar archive.

    `docker save -o <file.tar> <image name>`

7. To load a docker image from tar archive

    `docker load -i <file.tar>`