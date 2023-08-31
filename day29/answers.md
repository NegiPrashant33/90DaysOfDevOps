## Jenkins Important interview Questions.


1. What is the difference between Continuous Intefgration, Continuous Delivery and Continuous Deployment ?

    **Continuous Integration**
    
    Continuous Integration is a development practice where developers frequently integrate their code changes into a shared repository.  The primary goal of CI is to catch and address integration issues early in the development process. 

    As soon as the developer make changes to the codebase an automated build and test process is triggered.This process helps ensure that the newly introduced code integrates smoothly with the existing codebase and doesn't break the existing functionality. 


    **Continuous Delivery**

    Continuous Delivery extends the concept of Continuous Integration. It focuses on automating the entire software delivery pipeline, from code integration and testing to deployment to a staging or production environment. The key feature of CD is that the software is always in a deployable state. 
    
    This means that any changes that pass the automated tests in the CI process can be released to a production-like environment at any time, but the actual deployment to the live environment is still a manual decision. 

    **Continuous Deployment**

    Continuous Deployment takes the concept of Continuous Delivery a step further. In a Continuous Deployment approach, every change that passes the automated tests in the CI/CD pipeline is automatically deployed to the production environment without any manual intervention.


    ![cicd](/day29/images/cicd.png)


2. Benefits of CI/CD

    - CI helps in Early detection of integration issues, conflits and bugs.
  
    - With Continuous integration, the code quality remains consistent throughout the development process.

    - Continuous Delivery helps to market the application at a faster rate. 

    - Automated testing within the delivery pipeline ensures that releases are thoroughly tested before being deployed to users.

    - Continuous Delivery insures that the software updates are consistent and reliably deployed reducing the deployment errors and enhancing the user experience

    - Continuous Deployment futher automates the software delivery process by deploying the application to the production environment without any manual intervention.


3. What is meant by CI-CD ?

    **Continuous Integration (CI)** means that as developers work on their parts of a project, their code is frequently combined with everyone else's code. This is like making sure all the puzzle pieces fit together as you go, instead of waiting until the end. For example, if you and your friends are building a digital game, CI would be like regularly putting your pieces of the game together to see if everything works well.

    **Continuous Delivery (CD)** takes this idea further. It means that once the pieces of the game are put together and tested, they're ready to be given to players at any time. It's like having a kitchen where the chef has prepared the meal, and it just needs to be served when the customer is ready. So, in our game example, CD means that when a new feature is ready, it's prepared and tested in a way that it can be sent to players whenever the game makers decide.

    **Continuous Deployment (CD)** is like the fastest version of this process. In our game scenario, it's like putting the new game pieces out for players to enjoy as soon as they are created and tested, without waiting for the chef or waiter. So, if you fix a bug or add a new feature to the game, it's sent to players right away without delay.


4. What is a Jenkins Pipeline ?

    A pipeline is a collection of steps or jobs interlinked in a sequence.

    A Jenkins pipeline is a set of instructions, usually written as code, that defines how a software application is built, tested, and deployed. It's a way to automate and visualize the entire software delivery process, from integrating code changes to delivering the final product.

    **Pipeline syntax**

    ```groovy
    pipeline {
        agent any
        stages {
            stage('Build') {
                steps {
                    //
                }
            }
            stage('Test') {
                steps {
                    //
                }
            }
            stage('Deploy') {
                steps {
                    //
                }
            }
        }
    }
    ```


5. How do you configure a job in jenkins ?

    Refer [this](https://www.guru99.com/create-builds-jenkins-freestyle-project.html) blog on how to configure a new job in jenkins freestyle project.

    You can also [refer](/day23/tasks.md) to the previous challenges in order to understand how to configure a job in Jenkins
   

6. Where do you find errors in Jenkins?
    
    You can find errors in 

    - Build Console Output (failed builds)
    - Incorrect Job Configuration
    - Pipeline Script Errors

    Primarily the errors can be found out at the Build Console Output for a Jenkins Pipeline, Similarly if you create an Jenkins Agent, you can check the logs to find errors if why the agent is not connected.



7. In Jenkins how can you find log files?

    - Jenkins Web Interface
     
      - Log in to your Jenkins instance.
      - Click on "Manage Jenkins" on the main dashboard, then click on "System log"
      - This will open the system log viewer, where you can see recent logs and events related to Jenkins.

    - File System Location
        `/var/log/jenkins`, location for log files in the file system


8. Jenkins workflow and write a script for this workflow?

    A Jenkins workflow, often referred to as a Jenkins Pipeline, is a way to define and automate the entire software delivery process. It allows you to define a series of stages, steps, and actions that your code goes through from development to deployment.

    **Pipeline syntax**

    ```groovy
    pipeline {
        agent any
        stages {
            stage('Build') {
                steps {
                    //
                }
            }
            stage('Test') {
                steps {
                    //
                }
            }
            stage('Deploy') {
                steps {
                    //
                }
            }
        }
    }
    ```




9. How to create continuous deployment in Jenkins?


    ![resource](/day29/images/ci-4-1024x584.png)

    - Install Jenkins: Set up Jenkins and necessary plugins.

    - Connect to VCS: Link Jenkins to your version control system.

    - Define Pipeline: Create a Jenkinsfile or use visual editors.

    - Configure Deployment: Set up deployment environments.

    - Automate Stages: Define build, test, and deployment stages.

    - Automate Testing: Include automated tests in pipeline.

    - Deploy: If testing is successfull deploy the application

10. How to build a job in Jenkins?

    "Building a job" refers to the process of actually executing the steps defined in the job's configuration. Clicking "Build Now" triggers Jenkins to initiate the execution of the job according to the configuration you've set up. This might involve tasks like checking out code from a repository, compiling, testing, and producing artifacts.

11. Why we use pipeline in Jenkins?

    We use pipelines in Jenkins to automate and structure the entire software delivery process, from source code integration to deployment, enabling consistency, traceability, and efficient collaboration across development and operations teams.

    Pipeline is a powerful and flexible way to automate various tasks and processes involved in building, testing, and deploying software applications. Pipelines enable you to define the entire software delivery process as code, which can be versioned, reviewed, and maintained just like your application code

12. Is Only Jenkins enough for automation?

    While Jenkins is a powerful and widely used automation tool, it may not be sufficient for all automation needs, depending on the complexity and requirements of your projects.
    
    Jenkins is a versatile automation tool, the complexity and scope of your automation needs will determine whether it's sufficient on its own or if you need to complement it with other specialized tools to cover the full spectrum of automation tasks in your organization.

13. How will you handle secrets?

    In Jenkins, "secrets" refer to sensitive pieces of information, such as passwords, API tokens, private keys, and other credentials that are used by jobs, pipelines, and other automation tasks. 

    Refer [this](https://blog.gitguardian.com/how-to-handle-secrets-with-jenkins/) detailed blog to understand how to handle secrets in jenkins.


14. Explain different stages in CI-CD setup

    ![resource](/day29/images/cicd-pipeline-introduction-1024x422-1.jpg)

    Refer [this](https://semaphoreci.com/blog/cicd-pipeline) blog to understand the different stages in CI-CD. During our previous challenges that involved using Jenkins 


15. Name some of the plugins in Jenkin?

    - Git Plugin
    - Github Integration Plugin
    - Environment Injector Plugin
    - Docker Plugin
    - Kubernetes Plugin
    - Pipeline Plugin