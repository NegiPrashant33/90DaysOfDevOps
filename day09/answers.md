# Deep Dive into Git & GitHub for DevOps Engineers

## What is Git and why is it important ?

Git is a version control system. Git tracks the changes you make to files, so that you have a record of what has been done to the file, and you can also revert back to specific versions of the file. Git also makes collaboration easier, allowing changes by multiple people to all be merged into one source. 

Check out [why git](https://www.atlassian.com/git/tutorials/why-git) blog to understand the importance of using git.


## What is the difference between main and master branch ?

There is no difference between the main and master branch apart from their naming convention, the main/master branch is the primary/default branch for a repository in github, from which other branches are created. The main/master branch is considered the central line of development, and it is where the most up-to-date and tested version of the codebase resides.

Earlier the default branch or the primary branch was named as the master branch and now it's named as the main branch.

## Explain the difference between git and github ?

![Git vs Github](https://pbs.twimg.com/media/FgonU5LaAAECmzp.jpg)


Git provides functionality like version control system and source code management.

Github provides functionality of Git like VCS and SCM and has features of it's own too.


## How do you create a new repository in Github ?

This answer has been covered in [Day 8 exercise 1](https://github.com/NegiPrashant33/90DaysOfDevOps/blob/main/day08/answers.md#exercises) 

## What is difference between local & remote repository? How to connect local to remote? 

A local repository is a copy of a Git repository that resides on your local machine or development environment

A remote repository is a copy of a Git repository that is hosted on a remote server like GitHub


To connect local repository to remote 

- Suppose you have created a local repository named 90DaysOfDevOps, to track this repository using git we use the `git init` command
- In your local repository add the new files to the staging area and commit changes
    ```
    git add .

    git commit -m "Initial Commit"
    ```
- Now create a new repository with the similar name as the local repository on GitHub
- Now using the following commands we will connect the local repository to the remote repository and push the changes made to local to the remote repository
    ```
    git remote add origin <remote repository url>

    git push -u origin main
    ```

> Note: Refer [Day 8 exercise 3](https://github.com/NegiPrashant33/90DaysOfDevOps/blob/main/day08/answers.md#exercises) notes if you face errors while pushing changes to your remote repository


## Tasks

**Task 1:**

To set user name and email address associated with git commits

Use the following commands

`git config --global user.name "your user name"`

`git config --global user.email "your email id"`

You can use the `git config --list` command to check if the user name and email has been correctly set up.



**Task 2:**

- Create a new repository DevOps on GitHub, refer [Day 8 exercises](https://github.com/NegiPrashant33/90DaysOfDevOps/blob/main/day08/answers.md) to understand how to create a new repository
- To connect your local repository to the remote repository on github refer the above notes.
- Create a new file DevOps/Git/Day-02.txt
    ```shell
    # Go to the repository on your local machine
    # where you want to make the file

    cd /home/prashant/DevOps

    mkdir Git

    touch Day-02.txt
    ```

    Now we will add the files to the staging area, commit the changes and push those changes to the remote repository
    ```shell
    # To check the status of the local repository

    git status

    git add .

    git commit -m "Day-02 task completed"

    git push -u origin main
    ```

