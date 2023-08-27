# Day 23 Task: Jenkins Freestyle Project for DevOps Engineers.


1. **What is CI/CD ?**

2. **What Is a Build Job ?**

3. **What is Freestyle Projects ?**


## Task-01

- create a agent for your app. ( which you deployed from docker in earlier task )
- Create a new Jenkins freestyle project for your app.
- In the "Build" section of the project, add a build step to run the "docker build" command to build the image for the container.
- Add a second step to run the "docker run" command to start a container using the image created in step 3.

## Task-02

- Create Jenkins project to run "docker-compose up -d" command to start the multiple containers defined in the compose file ( Hint- use day-19 Application & Database docker-compose file )
- Set up a cleanup step in the Jenkins project to run "docker-compose down" command to stop and remove the containers defined in the compose file.

For Reference jenkins Freestyle Project visit [here](https://youtu.be/wwNWgG5htxs)