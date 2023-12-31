# Day 10 : Advance Git & GitHub for DevOps Engineers.

## Topics

1. **Git Branching**
2. **Git Revert and Reset Command**
3. **Git Rebase and Merge Command**

## Tasks Todo

### Task 1:
Add a text file called version01.txt inside the Devops/Git/ with “This is first feature of our application” written inside. 
This should be in a branch coming from `master`, 
[hint try `git checkout -b dev`], 
switch to `dev` branch ( Make sure your commit message will reflect as "Added new feature").
[Hint use your knowledge of creating branches and Git commit command]

- version01.txt should reflect at local repo first followed by Remote repo for review.
[Hint use your knowledge of Git push and git pull commands here] 

Add new commit in `dev` branch after adding below mentioned content in Devops/Git/version01.txt:
While writing the file make sure you write these lines

- 1st line>>  This is the bug fix in development branch
- Commit this with message “ Added feature2 in development branch”

- 2nd line>> This is gadbad code
- Commit this with message “ Added feature3 in development branch

- 3rd line>> This feature will gadbad everything from now.
- Commit with message “ Added feature4 in development branch

Restore the file to a previous version where the content should be “This is the bug fix in development branch”
[Hint use git revert or reset according to your knowledge]

### Task 2:

- Demonstrate the concept of branches with 2 or more branches with screenshot.
- add some changes to `dev` branch and merge that branch in `master`
- as a practice try git rebase too, see what difference you get.


## Note: 
We should learn and follow the [best practices](https://www.flagship.io/git-branching-strategies/) , industry follows for branching.

Simple Reference on branching: [video](https://youtu.be/NzjK9beT_CY)

Advance Reference on branching : [video](https://youtu.be/7xhkEQS3dXw)

You can Post on LinkedIn and let us know what you have learned from this task by #90DaysOfDevOps Challange. Happy Learning :)