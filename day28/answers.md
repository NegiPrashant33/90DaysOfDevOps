# Jenkins Agent

## Task 1

### Pre-requisite

- Create an EC2 instance
- Install java and jenkins in your server (make sure the java and jenkins version installed the master and slave server are same)

### Task Implementation

- For this task I will be using my local-machine as the Jenkins Master Server and we will setup an EC2 instance (Slave Server) for the Jenkins Agent

- In your local machine create a ssh key pair using the `ssh-keygen -t rsa` command, this will create a public and private key in your `.ssh/` directory.
    
    ![resource](/day28/images/Screenshot%20from%202023-08-30%2012-51-09.png)

- Copy the public key `id_rsa.pub` to the `authorized_keys` file of your `.ssh/` directory in the Slave Server. 

- Go to Manage Jenkins (Jenkins Master), go to Nodes and then click on New Node to create a Jenkins Agent

- Configure the Jenkins Agent (Node)

    ![resource](/day28/images/Screenshot%20from%202023-08-30%2012-59-42.png)

    In the credentials section click on add, then jenkins and configure the credentials details where you need to add the private key generated in the Master server earlier.

    ![resource](/day28/images/Screenshot%20from%202023-08-30%2012-59-59.png)

    ![resource](/day28/images/Screenshot%20from%202023-08-30%2013-45-28.png)

- In the logs section of the node you will see this message Agent successfully connected and online

    ![resource](/day28/images/Screenshot%20from%202023-08-30%2013-44-49.png)




## Task 2

- For this task configure your previous pipelines by adding the agent label. When this is done the job will be run by the jenkins agent

    ![resource](/day28/images/Screenshot%20from%202023-08-30%2013-59-41.png)