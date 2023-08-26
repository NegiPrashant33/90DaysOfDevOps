# Getting Started With Jenkins

## What is Jenkins ?

- Jenkins is an open source continuous integration-continuous delivery and deployment (CI/CD) automation software DevOps tool written in the Java programming language. It is used to implement CI/CD workflows, called pipelines.

- Jenkins is a tool that is used for automation, and it is an open-source server that allows all the developers to build, test and deploy software. It works or runs on java as it is written in java. By using Jenkins we can make a continuous integration of projects(jobs) or end-to-endpoint automation.

- Jenkins achieves Continuous Integration with the help of plugins. Plugins allow the integration of Various DevOps stages. If you want to integrate a particular tool, you need to install the plugins for that tool. For example Git, Maven 2 project, Amazon EC2, HTML publisher etc.

**Let us discuss the necessity of this tool before going ahead to the procedural part for installation:**

- Nowadays, humans are becoming lazy😴 day by day so even having digital screens and just one click button in front of us then also need some automation.

- Here, I’m referring to that part of automation where we need not have to look upon a process(here called a job) for completion and after it doing another job. For that, we have Jenkins with us.

Note: By now Jenkins should be installed on your machine(as it was a part of previous tasks, if not follow [Installation Guide](https://youtu.be/OkVtBKqMt7I))


## Tasks Todo

### Task 1

**Jenkins**

Jenkins is a tool that helps software developers automate various aspects of the software development lifecycle. It acts like a helpful robot that can perform tasks like building, testing, and deploying software applications automatically. These tasks are often repeated many times during the development process, and Jenkins takes away the burden by doing them consistently and quickly.


Let's take the example of a team working on a web application. Every time they make changes to the code, they need to build the application, run tests to ensure it works properly, and then deploy it to a testing server. Doing this manually can be time-consuming and error-prone.

Here's where Jenkins comes to the rescue:

- Code Changes: The developers make changes to the code and push it to a version control system like Git.

- Automated Trigger: Jenkins is set up to monitor this repository. As soon as changes are pushed, Jenkins detects them.

- Build: Jenkins automatically fetches the latest code, compiles it, and creates a build of the application.

- Testing: Jenkins runs a suite of tests on the newly built application to check for any issues or bugs.

- Deployment: If the tests pass successfully, Jenkins can then deploy the application to a testing server, making it available for further testing by the QA team.

- Notifications: Jenkins can also notify the team if any step fails. For example, if the tests don't pass, Jenkins can send an email or message to the developers, letting them know what went wrong.

By automating these steps, Jenkins ensures that the development process becomes smoother, faster, and less error-prone. Developers can focus on writing code and adding features, leaving the repetitive tasks to Jenkins.


**Bash Script to Install Jenkins**

```bash
#!/bin/bash

#################
# Author: Prashant Negi
# Date: 16 August 2023
#
# Purpose: Install java and jenkins
# Version: V1
#################


# Script set to debug mode
set -x

# Exit the script if any command fails
set -e

if [[ $EUID -ne 0 ]]; then
	echo "Script requires root user previliges"
	exit 1
fi


apt update

echo "Installing java"
apt install openjdk-17-jre -y

echo "Installing jenkins"
curl -fsSL https://pkg.jenkins.io/debian/jenkins.io-2023.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null

apt-get update

apt-get install jenkins -y

echo "Jenkins successfully installed"

```


### Task 2

**Creating a freestyle pipeline that says Hello World**

If you have installed jenkins in your local machine then you can access it using
`http://localhost:8080`

and If you have installed it on an EC2 instance then you can access it using
`http://<ipv4 address of your ec2 instance>:8080`

Make sure that port 8080 is exposed in your security group


![Unlock Jenkins](https://www.oreilly.com/api/v2/epubs/9781789130485/files/assets/5a9d2ce9-a6ca-414b-b7de-1e819314c893.png)

`cat <path>`

and give the Administrator Password, then setup your own password and username to access Jenkins.

- Create a new job, name the pipeline and select freestyle project.

- In the project configuration, click on Add Build Step

- Choose either Execute shell or Execute Windows batch command and enter the followind command

    `echo "Hello World`

- Save and run the pipeline by clicking on Build Now

- View the console output

    ![Console Output](/day22/images/Screenshot%20from%202023-08-26%2014-32-13.png)