# Basic Git & GitHub for DevOps Engineers

## What is Git?
Git is a version control system that allows developers to track changes made to their code over time, collaborate with other developers, and revert to previous versions if needed.

Git is installed and maintained on your local system rather than on the cloud. It focuses on version control, code sharing and have no user management tools. It is managed by Linux foundation and is open source software.

## What is Github?
GitHub is a web-based platform that provides hosting for version control using Git. It is a subsidiary of Microsoft, and it offers all of the distributed version control and source code management (SCM) functionality of Git as well as adding its own features. GitHub is a very popular platform for developers to share and collaborate on projects, and it is also used for hosting open-source projects.

Github is a platform for hosting and collaborating on git repositores.

## What is Version Control? How many types of version controls we have?
Version control is a system that tracks changes to a file or set of files over time so that you can recall specific versions later. It allows you to revert files back to a previous state, revert the entire project back to a previous state, compare changes over time, see who last modified something that might be causing a problem, who introduced an issue and when, and more.

There are two main types of version control systems: centralized version control systems and distributed version control systems.

1) A centralized version control system (CVCS) uses a central server to store all the versions of a project's files. Developers "check out" files from the central server, make changes, and then "check in" the updated files. Examples of CVCS include Subversion and Perforce.

2) A distributed version control system (DVCS) allows developers to "clone" an entire repository, including the entire version history of the project. This means that they have a complete local copy of the repository, including all branches and past versions. Developers can work independently and then later merge their changes back into the main repository. Examples of DVCS include Git, Mercurial, and Darcs.


## Why we use distributed version control over centralized version control? 

1) Better collaboration: In a DVCS, every developer has a full copy of the repository, including the entire history of all changes. This makes it easier for developers to work together, as they don't have to constantly communicate with a central server to commit their changes or to see the changes made by others.

2) Improved speed: Because developers have a local copy of the repository, they can commit their changes and perform other version control actions faster, as they don't have to communicate with a central server.

3) Greater flexibility: With a DVCS, developers can work offline and commit their changes later when they do have an internet connection. They can also choose to share their changes with only a subset of the team, rather than pushing all of their changes to a central server.

4) Enhanced security: In a DVCS, the repository history is stored on multiple servers and computers, which makes it more resistant to data loss. If the central server in a CVCS goes down or the repository becomes corrupted, it can be difficult to recover the lost data.


## Exercises

**1:** 

- Login to your github account and click on the plus icon on the right hand side of your window, click on create a new repository, fill out the necessary details and click on create repository
- a new repository will be created, click on the green colored button named code, you will have different options to clone your remote repository to your local machine such as https, ssh, github cli.
- copy the repository url either from https or ssh.
- go to your system terminal and enter the command
    ```shell
    git clone <repository url>
    ```

Make sure git is installed in your system


**2:**

**Git Life Cycle**

![git workflow](https://i.redd.it/nm1w0gnf2zh11.png)

To make some changes to a file in a repository and commit the changes

```shell
# Add a new file to the repository cloned locally
# Add new content to the file
vim notes.txt

# Adding the file to the staging area
git add notes.txt

# Commiting the changes
git commit -m "Notes added"
```


**3:**
```shell
# Push the changes to the main branch of the remote repository
git push -u origin main
```


> Note: If you come across an error such as `Fatal: Could not read from remote repository` then refer [this](https://youtu.be/uFaYgSVzy3w) youtube video and if you come across an error that says `SSH permission denied`, then refer [this](https://youtu.be/Irj-2tmV0JM) youtube video 



> Note: While completing the task 8 I made a mistake of giving a wrong commit description as "Day 9 completed" instead of "Day 8 completed" (keep in mind I did not push the commit to the remote repository). This mistake can be resolved using `git commit --amend` command, which opens up an editor for you where you can change your commit message and save changes