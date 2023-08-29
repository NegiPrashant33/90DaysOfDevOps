# Complete Jenkins CI/CD Project With GitHub Integration

**Complete Project Implementation (this will cover both Task 1 and Task 2)**


## Table Of Content-
- [Complete Jenkins CI/CD Project With GitHub Integration](#complete-jenkins-cicd-project-with-github-integration)
  - [Table Of Content-](#table-of-content-)
  - [Project Overview](#project-overview)
  - [Tools/Technologies Used](#toolstechnologies-used)
  - [Pre-requisite](#pre-requisite)
  - [Project Implementation](#project-implementation)
    - [EC2 Instance and Tools Setup](#ec2-instance-and-tools-setup)
    - [Jenkins Configuration](#jenkins-configuration)
    - [Github and Jenkins Integration](#github-and-jenkins-integration)
    - [Build the Job](#build-the-job)
    - [Containerization With Docker](#containerization-with-docker)
    - [Automated Pipeline Trigger (Webhook)](#automated-pipeline-trigger-webhook)



## Project Overview

In this project, we'll establish an end-to-end CI/CD pipeline using Jenkins, AWS EC2, and GitHub. The pipeline automates the process of taking code from GitHub, containerizing it using Docker, and deploying it on an AWS EC2 instance.

The pipeline will also be connected to GitHub through webhooks, enabling automatic triggering of builds upon code changes.


## Tools/Technologies Used

- Docker
- Github
- AWS EC2 instance
- Jenkins

## Pre-requisite

- Should know how to launch and EC2 instance on AWS
- Install Docker, Java, Jenkins on the created EC2 instance
- Make sure to add the current user and the jenkins user (of the Liuux OS) to the docker group in order to provide necessary permissions.

## Project Implementation


### EC2 Instance and Tools Setup

- Fork the following repository [github](https://github.com/LondheShubham153/node-todo-cicd)
   
- Launch an EC2 instance and install docker, java, jenkins on it
   
- Use the scripts (docker.sh and jenkins.sh) to install docker, java, jenkins from my repository [github](https://github.com/NegiPrashant33/scripts)
   
- Check the /etc/group directory to see if the the current user and the jenkins user is added to the docker group if not use the following commands
    
    ```bash
    sudo usermod -aG docker $USER
    
    sudo usermod -aG docker jenkins
    ```
    
- Check if jenkins is running on the instance or not using the following command
    
    ```bash
    systemctl status jenkins
    ```
    

### Jenkins Configuration

- Access jenkins server from your browser using `http://<ipv4 address of your EC2 instance>:8080` (make sure you have made the necessary changes to your Security Group in order to access the Jenkins Server)


- Create a new job (new item) in the Jenkins Server


- todo-node-app (freestyle project)
    
    ![resource](/day24/images/Screenshot%20from%202023-08-28%2010-20-10.png)
    
- Configure the new job
    
    
    Add github project url
    
    ![resource](/day24/images/Screenshot%20from%202023-08-28%2010-21-41.png)


### Github and Jenkins Integration
    
In the Source Code Section we will Select Git 

- Add the git url you have forked
- Create credentials
- In your EC2 instance create public and private keys using the following commands (in order for your github to access the EC2 instance/remote server we will use the SSH secure shell method)
    
    ```bash
    ssh-keygen -t rsa
    
    cd .ssh/
    
    # private key
    cat id_rsa 
    
    # public key
    cat id_rsa.pub
    ```
    
    ![resource](/day24/images/Screenshot%20from%202023-08-28%2010-31-25.png)
    
- Go to your Github setting, in your SSH and GPG Keys section, create a new SSH key and add your public key
    
    ![resource](/day24/images/Screenshot%20from%202023-08-28%2010-30-54.png)
    
- Now add the private key to your credentials section
    
    Click on add —> jenkins
    

    ![resource](/day24/images/Screenshot%20from%202023-08-28%2010-35-22.png)

    ![resource](/day24/images/Screenshot%20from%202023-08-28%2010-35-32.png)

    ![resource](/day24/images/Screenshot%20from%202023-08-28%2010-35-54.png)

The whole process will integrate github and jenkins.


### Build the Job

- Build the job by clicking on build now and then check the console output
    
    
    ![resource](/day24/images/Screenshot%20from%202023-08-28%2010-42-52.png)
    
    You will see an output like this
    
    You can access the Building in Workspace path in your EC2 instance to see that the code has been to that directory
    
    ![resource](/day24/images/Screenshot%20from%202023-08-28%2010-44-11.png)
    
- In your EC2 instance run the commands mentioned in the [README.md](http://README.md) file of the forked repository
    
    ```bash
    sudo apt install nodejs
    
    sudo apt install npm
    
    sudo npm install
    
    node app.js
    ```
    

- Access your application on the 8000 port

    `http://<ipv4 address of your ec2 instance>:8000/`
    

    ![resource](/day24/images/Screenshot%20from%202023-08-28%2010-54-43.png)

With this we will only be able to access our application while we are running the above commands(manual work) therefore we will containarize our application using Docker.

### Containerization With Docker

- Create a dockerfile on your own for the application or use the existing dockerfile in the github repo
    
    
    ```bash
    docker build -t node-todo-app .
    
    docker run -d --name node-todo-app -p 8000:8000 node-todo-apps
    ```
    
    Configure your jenkins job again to automate the whole process of getting the code form github and containerizing the application.
    
    ![resource](/day24/images/Screenshot%20from%202023-08-28%2011-39-48.png)
    
    and build your job.


### Automated Pipeline Trigger (Webhook)
    
- Now we will automate the task of building jobs in Jenkins, as for now we were manually building our job by clicking on build now
    
    
    We will automate this task such that any changes made to the github repository (code base) will automatically trigger the build process (jenkins pipeline)
    
    Install github integration plugin in jenkins
    
    Configure your jenkins job again
    
    ![resource](/day24/images/Screenshot%20from%202023-08-28%2016-47-40.png)
    
    Go to your repository settings and add a webhook
    
    Your payload url will be your jenkins url with an addtional parameter 
    
    `http://<ipv4 address of EC@ instance>:8080/github-webhook/`
    
    ![resource](/day24/images/Screenshot%20from%202023-08-28%2016-48-35.png)
    
    A green tick specifies that the Webhook is working and as soon as you make any changes to your code base in github the jenkins pipeline will be triggered and build will take place automatically
    
    ![resource](/day24/images/Screenshot%20from%202023-08-28%2016-50-45.png)