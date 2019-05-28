---
title: "Procedure – Version Control"
draft: true
documents: ['Procedure']
---

## Branches

- Manage branches using an approach roughly based on [gitflow](https://nvie.com/posts/a-successful-git-branching-model/).
- Every project should have the following branches:
    * `master`
    * `dev`
- Feature branches should be made off `dev`.
    - From the `master` branch, switch to `dev` branch:
    ```{r}
    $ git checkout dev
    ```
    - Pull any changes from the cloud repository:
    ```{r}
    $ git pull
    ```
    - Create the new branch off of `dev` with:
    ```{r}
    $ git checkout -b <new_feature_branch_name>
    ```
    - As a final step, push the branch back to the cloud with and set tracking:
    ```{r}
    $ git push origin <new_feature_branch_name>
    $ git branch --set-upstream-to=origin/<new_feature_branch_name> <new_feature_branch_name>
    ```
- To push local changes to origin
    - First check the status of local files
    ```{r}
    $ git status
    ```
    - Add local changes and commit them with a message
    ```{r}
    $ git add dir/file.extension
    $ git commit -m "Your message goes here"
    ```
    - Pull any changes from `dev` branch, so branch can be merged directly into dev if features are complete
    ```{r}
    $ git pull origin dev
    ```
    - Push back to the cloud repository
    ```{r}
    $ git push origin <new_feature_branch_name>
    ```
    
- You should never have more than two feature branches active.

## Merge/Pull Requests Requests

- Code should be thoroughly tested before a request is initiated.
    - Tests should be conducted with an *empty* environment.
        - From RStudio terminal, clean all objects from the workspace
        ```{r}
        $ rm(list=list())
        ``` 
        - Restart your R session with
        Ctrl+Shift+F10
- Create a merge request on [gitlab](https://gitlab.com/exegetic) or [github](https://github.com/datawookie/www-exegetic-biz)
    - Navigate to the merge request tab 
    - Select the source branch to merged and the destination branch, which is usually develop
    - Under the "Assignee", assign the merge request to the relevant project leader