---
 title: "Procedure – Version Control"
draft: true
documents: ['Procedure']
---
  
## Connecting to a remote repository
  
- To connect to repoostory, or contribute to a certain repository, create a local copy with:
```{r}
$ git clone https://gitlab.com/exegetic/<repository_name>.git
```
- Git will automatically create a connection between your local copy and the cloud, creating a "remote" called origin. Check the the status of this connection with
```{r}
$ cd <repository_name>
$ git remote -v
origin	https://gitlab.com/exegetic/<repository_name>.git (fetch)
origin	https://gitlab.com/exegetic/<repository_name>.git (push)
```
This states the if we make any changes and "push" to the cloud repository, or the "origin", this will be to the location specified above. Similarily if we "pull" any changes made by others on the same repository into our copy, we will "pull" changes made to the "origin" into our copy of the repository.

## Pulling/Pushing to a remote repository

- To push local changes to the origin, first check the status of local files
```{r}
$ git status
```
- Add any local changes and commit them to the staging area with a message
```{r}
$ git add dir/file.extension
$ git commit -m "Your message goes here"
```
- Pull any changes from `dev` branch, so branch can be merged directly into `dev` if features are complete
```{r}
$ git pull origin dev
```
- Push back the local changes to the origin
```{r}
$ git push origin <new_feature_branch_name>
  ```

## Branches

- Manage branches using an approach roughly based on [gitflow](https://nvie.com/posts/a-successful-git-branching-model/).
- Every project should have the following branches:
* `master`
* `dev`
- Feature branches should be made off `dev`
    - To create a new feature branch off of `dev`, first switch to `dev` branch:
    ```{r}
    $ git checkout dev
    ```
    - Pull any changes from the cloud repository:
    ```{r}
    $ git pull origin dev
    ```
    - Create the new branch off of `dev` with:
    ```{r}
    $ git checkout -b <new_feature_branch_name>
    ```
    - As a final step, push the new branch back to the cloud with and set up tracking:
    ```{r}
    $ git push origin <new_feature_branch_name>
    $ git branch --set-upstream-to=origin/<new_feature_branch_name> <new_feature_branch_name>
      ```

- If you have forgotten to create a feature branch and have made changes to a non-feature branch, for instance `dev`
    - First, stash your changes:
    ```{r}
    $ git stash
    ```
    - Create a new branch as detailed above
    - Check that you are on the new branch
    ```{r}
    $ git status
    ```
    - Reapply your changes to the new branch
    ```{r}
    $ git stash pop
    ```
    - Commit your changes as detailed above

- You should never have more than two feature branches active.

## Merge requests

- Code should be thoroughly tested before a request is initiated.
- Tests should be conducted with an *empty* environment.
- From RStudio terminal, clean all objects from the workspace
```{r}
$ rm(list=list())
``` 
- Restart your R session with Ctrl+Shift+F10
- Create a merge request on [Gitlab](https://gitlab.com/exegetic) or [Github](https://github.com/datawookie/www-exegetic-biz)
- Navigate to the merge request tab 
- Select the source branch to merged and the destination branch, which is usually *develop*
- Under the "Assignee", assign the merge request to the relevant project leader

