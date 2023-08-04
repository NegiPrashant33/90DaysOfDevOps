# Advanced Git and GitHub for DevOps Engineer

## Git Branching
Git branching is a feature of the version control system Git that allows you to create separate lines of development within a Git repository. It enables you to work on different features, bug fixes, or experiments in isolation from the main codebase.

Each branch represent an independent line of developement. 
Each repository has one default branch, and can have multiple other branches. You can merge a branch into another branch using a pull request.


Some important commands related to git branching

- `git branch <branch name>`: to create a new branch.
- `git branch`: to view list of available branches.
- `git checkout <branch name>`: to switch to a different branch.
- `git checkout -b <branch name>`: to create a new branch and switch to it.
- `git merge <branch name>`: to merge a branch, the branch mentioned will be merged to the current branch where the user is at.
- `git branch -d <branch name>`: to delete a branch.


> Note: Refer this [Learn Git Branching](https://learngitbranching.js.org/) amazing website to learn about branching and the various concept related to it.

## Git Revert and Reset

git revert and git reset are two Git commands used to undo changes in a repository's history, but they work in different ways and have different consequences. 

### Git Revert

git revert is used to create a new commit that undoes the changes introduced by a specific commit.


It is a safe way to undo changes because it does not modify the existing commits in the history. Instead, it adds new commits that effectively revert the changes made in the specified commit.
This means that the commit history remains intact, and you can still see the original commit and the subsequent revert commit.

`git revert <commit-hash>`

### Git Reset

git reset is used to move the branch pointer to a specific commit, effectively resetting the branch to that commit. It has several options (--soft, --mixed, and --hard), each with different consequences.

`git reset [--soft | --mixed | --hard] <commit-hash>`


## Git Rebase and Merge


git rebase and git merge are two different ways to combine changes from one branch into another in Git. They have different purposes and effects on the commit history.

### Git Rebase

git rebase rewrites the commit history to apply the changes on top of another branch, resulting in a cleaner and more linear history

### Git Merge

git merge creates a new merge commit to combine changes from different branches, resulting in a commit history that reflects the branching and merging process


Refer to this article for a better understanding of Git Rebase and Merge [Read here](https://www.simplilearn.com/git-rebase-vs-merge-article)



## Tasks

### Task 1

- Create a new directory locally DevOps, and then create a new repository on GitHub as DevOps, connect the local repository to the remote (refer the previous tasks for day 8 and 9 to understand how to do this)
- Create a new file README.md then add, commit and push the changes to the remote repository
- Now as the task given create a new branch and follow the instructions
    ```shell
    mkdir Git

    # Create a new branch and switch to it
    git checkout -b dev

    # To check if you are at the desired branch use command
    git branch

    # Create file version01.txt and add specified content
    vim version01.txt

    # Stage the file
    git add Git/version01.txt

    # Commit changes
    git commit -m "Added new feature"

    # Push changes to remote repository
    git push -u origin dev
    ```
- Adding new commits according to the task and then reverting back to the specified version of the file
    ![Task content](/day10/images/Screenshot%20from%202023-08-01%2012-27-23.png)
- Now Restore the file to a previous version where the content should be “This is the bug fix in development branch”, this can be done in two ways, using `git revert` and `git reset` command
    ```shell
    git revert <commit hash of 4th commit>

    git revert <commit hash of 3rd commit>
    ```

    or

    ```shell
    git reset --hard <commit hash of 2nd commit>
    ```

>Note: `git revert` reverts a specific commit by creating a new commit that undoes the changes introduced by that commit. It is a safe way to undo changes, as it leaves a clear history of the reversion, while `git reset` moves the branch pointer to a specified commit, effectively removing subsequent commits from the branch's history, it rewrites the commit history.


## Task 2

- A branch is an independent line of development which enables us to work on different features, bug fixes, or experiments in isolation from the main codebase. Here we have 2 branches main and dev, the main branch is the primary line of development which consist of revised and most updated version of our codebase
    ![Task content](/day10/images/Screenshot%20from%202023-08-01%2017-14-29.png)
- Merging the dev branch to the main branch
    ```shell
    # Switch to the main branch
    git checkout main

    # Merge
    git merge dev

    # After the merge is completed, push changes to remote repository
    git push -u origin main
    ```
- `git rebase` is used when you want a clean and linear history of your commits

    Here if we are on the dev branch and perform the below command then, the changes in the main branch will be integrated with the feature branch which will now have a linear commit history

    ```shell
    git rebase main
    ```