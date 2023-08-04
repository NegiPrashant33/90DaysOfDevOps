# Advance Git & GitHub for DevOps Engineers: Part-2

## Git Stash:
Git stash is a command that allows you to temporarily save changes you have made in your working directory, without committing them. This is useful when you need to switch to a different branch to work on something else, but you don't want to commit the changes you've made in your current branch yet.

To use Git stash, you first create a new branch and make some changes to it. Then you can use the command `git stash` to save those changes. This will remove the changes from your working directory and record them in a new stash. You can apply these changes later. git stash list command shows the list of stashed changes.

To restore the temporarily stored working directory we use the `git stash pop` command.

You can also use `git stash drop` to delete a stash and `git stash clear` to delete all the stashes.

## Cherry-pick:
Git cherry-pick is a command that allows you to select specific commits from one branch and apply them to another. This can be useful when you want to selectively apply changes that were made in one branch to another.

To use git cherry-pick, you first create two new branches and make some commits to them. Then you use `git cherry-pick <commit_hash>` command to select the specific commits from one branch and apply them to the other.

## Resolving Conflicts:
Conflicts can occur when you merge or rebase branches that have diverged, and you need to manually resolve the conflicts before git can proceed with the merge/rebase.


`git status` command shows the files that have conflicts, `git diff` command shows the difference between the conflicting versions and git add command is used to add the resolved files.


## Tasks

### Task 1

- To create a new branch and make some changes to it
    ```shell
    git checkout dev

    # Add some content
    vim feature01.txt
    ```
- When you use `git status`, you will see the changes made to the new branch, it will tell us that feature01.txt file is modified, now to save this work without committing it we use `git stash`
    ```shell
    git status

    git stash
    ```
- Switch to a different branch, make some changes and commit them.
    ```shell
    git checkout main

    vim README.md

    git add README.md

    git commit -m "Added README file"
    ```
- Use git stash pop to bring the changes back and apply them on top of the new commits.
    ```shell
    git checkout dev

    # To pull the changes from main branch
    git pull origin main

    git stash pop

    git add feature01.txt

    git commit -m "Added new feature 1"

    git push -u origin dev
    ```


### Task 2

- Make the specified changes in the task to the version01.txt file, make sure that it is done in the dev branch
- Now all the commit messages showing in the feature branch log, should be reflected in Production branch too which will come out from main branch
    ```shell
    git checkout -b prod

    git branch

    git rebase dev
    ```

### Task 3