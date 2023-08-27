# Jenkins Freestyle Project for DevOps Engineers.

## What is CI/CD ?

- **CI or Continuous Integration** is the practice of automating the integration of code changes from multiple developers into a single codebase. It is a software development practice where the developers commit their work frequently into the central code repository (Github or Stash). Then there are automated tools that build the newly committed code and do a code review, etc as required upon integration.

    The key goals of Continuous Integration are to find and address bugs quicker, make the process of integrating code across a team of developers easier, improve software quality and reduce the time it takes to release new feature updates.

- **CD or Continuous Delivery** is carried out after Continuous Integration to make sure that we can release new changes to our customers quickly in an error-free way. This includes running integration and regression tests in the staging area (similar to the production environment) so that the final release is not broken in production. It ensures to automate the release process so that we have a release-ready product at all times and we can deploy our application at any point in time.

- Difference between **Continuous Delivery and Continuous Deployment**

    - Continuous Delivery: In Continuous Delivery, the decision to release to production is a manual one. Once changes pass automated tests, they are considered deployable, but the deployment itself requires human approval.

    - Continuous Deployment: In Continuous Deployment, there is no manual decision-making step. Changes that pass automated tests are automatically deployed to production without human intervention.

## What Is a Build Job ?

A Jenkins build job contains the configuration for automating a specific task or step in the application building process. These tasks include gathering dependencies, compiling, archiving, or transforming code, and testing and deploying code in different environments.

Jenkins supports several types of build jobs, such as freestyle projects, pipelines, multi-configuration projects, folders, multibranch pipelines, and organization folders.

## What is Freestyle Projects ? 

A freestyle project in Jenkins is a type of project that allows you to build, test, and deploy software using a variety of different options and configurations. 

# Tasks Todo

## Task 1

Before setting up an agent in jenkins, read [this](https://medium.com/edureka/jenkins-master-and-slave-architecture-e3d6c4728945) blog on How the jenkins master slave architecture work.

**Jenkins Master:** The Jenkins Master is the central server that handles the management of jobs, scheduling, user management, and overall coordination of the build and automation processes.

**Jenkins Agent (Slave):** Agents, also referred to as slaves, are separate worker nodes that perform the actual build and automation tasks. They are responsible for executing jobs that are scheduled by the master. Agents can run on different machines, operating systems, or even cloud instances.

**Communication:** The Jenkins Master communicates with the Agents using a combination of pull and push mechanisms. The master can push work (jobs) to agents, and agents pull work from the master. Agents execute the tasks, and the results are reported back to the master.

**Why Master Slave architecture is required**

- Scalability: In a Jenkins Master-Slave architecture, multiple agents can handle tasks concurrently, allowing for better utilization of resources and faster job execution. This is particularly beneficial when dealing with a large number of jobs or resource-intensive tasks.

- Resource Isolation: Agents can be configured on different hardware, operating systems, or cloud environments. This allows for better resource isolation and the ability to run builds in diverse environments.

- Distributed Workloads: By distributing work among agents, the Jenkins Master is relieved from the burden of executing all jobs. This improves the responsiveness of the master and reduces the likelihood of bottlenecks.

- Parallelism: With multiple agents, jobs can be executed in parallel, leading to faster builds and quicker feedback.

- Specialized Environments: Certain jobs might require specific environments or tools that are not available on the master. Agents can be set up to cater to these requirements.

- Redundancy: Having multiple agents ensures redundancy. If one agent fails, the jobs can be automatically routed to other available agents.

- Resource Management: Agents can be dynamically provisioned and scaled based on demand. This efficient use of resources can save time and costs.



Setting Up jenkins agent (Master-Slave architecture)

- Launch an EC2 instance and install jenkins on it, start the jenkins server (configure the EC2 instance security group inbound rules in order to access jenkins at port 8080, futher the project configure the SG accordingly in order to access the desired port in order to run you applicaiton)

- To to manage jenkins, and click on new node to create a new agent that will take permission from the master (built in node) to execute the given task/job.

- Configure the new node

    ![Configuration](/day23/images/Screenshot%20from%202023-08-27%2012-39-29.png)

    ![Configuration](/day23/images/Screenshot%20from%202023-08-27%2012-58-43.png)

    ![Configuration](/day23/images/Screenshot%20from%202023-08-27%2012-58-59.png)

    ![Configuration](/day23/images/Screenshot%20from%202023-08-27%2012-59-34.png)

- Clone the following repository to your EC2 instance

    `git clone https://github.com/LondheShubham153/django-notes-app`

- Create a new item (new job) for your Jenkins server and select freestye project

- Configure the new job
    > Note: Make sure you have added jenkins, current user to the docker group, you can install both jenkins and docker using the script in my github repository named (docker.sh and jenkins.sh) https://github.com/NegiPrashant33/scripts

    ![New Job](/day23/images/Screenshot%20from%202023-08-27%2013-26-50.png)

- Give necessary permission to the jenkins agent `chmod 777 /home/ubuntu`

     `chmod 777 django-notes-app` in order for jenkins agent to run

- Check your console output for any erros, if the build is successfull then you can access your application

    ![Django Application](/day23/images/Screenshot%20from%202023-08-27%2013-43-44.png)


## Task 2

Using the same github repository from the previous task and the same steps as well

- In the build step modify the commands and use the following command instead of docker build and run

    `docker-compose up -d`

- In the post build actions set up the clean up command

    `docker-compose down`