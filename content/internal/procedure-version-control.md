---
title: "Procedure – Version Control"
draft: true
documents: ['Procedure']
---


### Glossary
- **Repository**: Collection of code that functions as a self-standing unit - also called a package.
- **Remote**: A common copy repository all team members use to exchange their work, *usually* hosted on a cloud service.
- **Branch**: A copy of a repository that is built off of the main copy, with a unique name and it's own set of changes.
- **Merge request**: A request made by a user to a repository's maintainers to incorporate the user's changes, usually presented a feature branch, into the main working branch which is usually the develop branch `dev` - also called a *Pull request* (on Github). 
  
  
## Connecting To A Remote Repository
  
- To connect to repoostory, or contribute to a certain repository, create a local copy with:
```{r}
$ git clone https://gitlab.com/exegetic/<repository_name>.git
```
- Git will automatically create a connection between your local copy and the cloud, creating a "remote" called origin. Check the the status of this connection with:
```{r}
$ cd <repository_name>
$ git remote -v
origin	https://gitlab.com/exegetic/<repository_name>.git (fetch)
origin	https://gitlab.com/exegetic/<repository_name>.git (push)
```
This states the if we make any changes and "push" to the cloud repository, or the "origin", this will be to the location specified above. Similarily if we "pull" any changes made by others on the same repository into our copy, we will "pull" changes made to the "origin" into our copy of the repository.


## Connecting Existing Local Repository To A Remote Repository
- To connect an existing local repository to the cloud, create an empty project by following this [guide](https://docs.gitlab.com/ee/gitlab-basics/create-project.html#blank-projects).
    - **DO NOT** initialize the `README`, `license` or `gitignore` files
    - Ensure the name of the project is the same as the directory name of the local repository.
- Change directory to the existing local project and initialize it as a Git repository.
```{r}
$ cd <repository_name>
$ git init
Initialized empty Git repository in /home/user/<repository_name>/.git/
```
- Connect the local repository to the remote repository.
```{r}
$ git remote add origin git@gitlab.com:exegetic/<repository_name>.git
```
- Create a `README.md`  file.
```{r}
$ touch `README.md`
```
- Add local files.
```{r}
$ git add README.md other_files.extensions
```
- Commit the relevant files to the staging area with a commit message.
```{r}
$ git commit -m "Initial commit"
[master (root-commit) aBa00aba] Initial commit
 X files changed, X insertions(+)
 create mode 1001001 README.md other_files.extensions
```
- Push the files to the remote repository.
```{r}
$ git push -u origin master 
```


## Pulling/Pushing To A Remote Repository

- To push local changes to the origin, first check the status of local files.
```{r}
$ git status
On branch <branch_name>
Changes not staged for commit:
(use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   directory/<filename>.extension
```
- Add any local changes.
```{r}
$ git add directory/<filename>.extension
```
- Commit them to the staging area with an infomative message.
```{r}
$ git commit -m "Resolved the issue where tabpanel 'summary' would not display until a driver was selected"
```
- Pull any changes from `dev` branch, so branch can be merged directly into `dev` if features are complete.
```{r}
$ git pull origin dev
```
- Push back the local changes to the origin.
```{r}
$ git push origin <new_feature_branch_name>
```


## Branches

- Manage branches using an approach roughly based on [gitflow](https://nvie.com/posts/a-successful-git-branching-model/).
- Every project should have the following branches:
    * `master`
    * `dev`
- Feature branches should be made off `dev`:
    - To create a new feature branch off of `dev`, first switch to `dev` branch.
    ```{r}
    $ git checkout dev
    ```
    - Pull any changes from the cloud repository.
    ```{r}
    $ git pull origin dev
    ```
    - Create the new branch off of `dev`.
    ```{r}
    $ git checkout -b <new_feature_branch_name>
    ```
    - As a final step, push the new branch back to the cloud with and set up tracking.
    ```{r}
    $ git push origin <new_feature_branch_name>
    $ git branch --set-upstream-to=origin/<new_feature_branch_name> <new_feature_branch_name>
      ```

- If you have forgotten to create a feature branch and have made changes to a non-feature branch, for instance `dev`:
    - First, stash your changes.
    ```{r}
    $ git stash
    ```
    - Create a new branch as detailed above.
    - Check that you are on the new branch.
    ```{r}
    $ git status
    On branch <new_feature_branch_name>
    ```
    - Reapply your changes to the new branch.
    ```{r}
    $ git stash pop
    ```
    - Commit your changes as detailed above.

- You should never have more than two feature branches active.
 
 
## Merge Requests

- Code should be thoroughly tested before a request is initiated.
- Tests should be conducted with an *empty* environment:
    - In R:
        - From RStudio terminal, clean all objects from the workspace.
        ```{r}
        $ rm(list=list())
        ``` 
        - Restart your R session with Ctrl+Shift+F10.
    - In Python:
        - In VSCode, clear all variables by restarting the IPython kernel (top right of the interactive window).
        - Run the entire script by right-clicking and selection "Run All Cells".
- Create a merge request on [Gitlab](https://gitlab.com/exegetic) or [Github](https://github.com/datawookie/www-exegetic-biz).
- Navigate to the merge request tab.
- Select the source branch to merged and the destination branch, which is usually *develop*.
- Under the "Assignee", assign the merge request to the relevant project leader.

