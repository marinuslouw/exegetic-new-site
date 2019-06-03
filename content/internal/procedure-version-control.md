---
title: "Procedure – Version Control"
draft: true
documents: ['Procedure']
---


### Glossary
  
- **Repository**: Collection of code that functions as a self-standing unit - also called a package.
- **Remote**: A common copy repository all team members use to exchange their work, *usually* hosted on a cloud service.
- **Branch**: A copy of a repository, usually built off of a high-level version of a repository, than can be changed independently of other copies of the same repository. A `branch` has a unique name and it's own set of changes that can be `merged` into back into the high-level version of the repository.
- **Merge request**: A request made by a user to a repository's maintainers to incorporate the user's changes, usually presented a feature branch, into the main working branch which is usually the develop branch `dev` - also called a *Pull request* (on Github). 


## Connecting To A Remote Repository

To connect to repoostory, or contribute to a certain repository, create a local copy with:

```{r}
$ git clone https://gitlab.com/exegetic/<repository_name>.git
```

Git will automatically create a connection between your local copy and the cloud, creating a "remote" called origin. Check the the status of this connection with:

```{r}
$ cd <repository_name>
$ git remote -v
origin	https://gitlab.com/exegetic/<repository_name>.git (fetch)
origin	https://gitlab.com/exegetic/<repository_name>.git (push)
```

This states that if we make any changes and "push" to the cloud repository, or the "origin", this will be to the location specified above. Similarily if we "pull" any changes made by others on the same repository into our copy, we will "pull" changes made to the "origin" into our copy of the repository.


## Connecting Existing Local Repository To A Remote Repository

To connect an existing local repository to the cloud, first create an empty project by following this [guide](https://docs.gitlab.com/ee/gitlab-basics/create-project.html#blank-projects).

* **DO NOT** initialize the `README`, `license` or `gitignore` files.
* Ensure the name of the project on the cloud service is the same as the directory name of the local repository.

Change the current working directory to the existing local project and initialize it as a Git repository.

```{r}
$ cd <repository_name>
$ git init
Initialized empty Git repository in /home/user/<repository_name>/.git/
```

Connect the local repository to the remote repository.

```{r}
$ git remote add origin git@gitlab.com:exegetic/<repository_name>.git
```

Create a `README.md`  file.

```{r}
$ touch README.md
```

Add the existing other local files.

```{r}
$ git add README.md other_files.extensions
```

Commit the relevant files to the staging area with a commit message.

```{r}
$ git commit -m "Initial commit"
[master (root-commit) aBa00aba] Initial commit
X files changed, X insertions(+)
create mode 1001001 README.md other_files.extensions
```

Push the files to the remote repository.

```{r}
$ git push -u origin master 
```


## Pulling/Pushing To A Remote Repository

To push local changes to the origin, first check the status of local files.

```{r}
$ git status
On branch <branch_name>
Changes not staged for commit:
(use "git add <file>..." to update what will be committed)
(use "git checkout -- <file>..." to discard changes in working directory)

modified:   directory/<filename>.extension
```

Add any local changes.

```{r}
$ git add directory/<filename>.extension
```

Commit them to the staging area with a commit message.

```{r}
$ git commit -m "Your message here"
```

Pull any changes from `dev` branch, so branch can be merged directly into `dev` if features are complete.

```{r}
$ git pull origin dev
```

Push back the local changes to the origin.

```{r}
$ git push origin <new_feature_branch_name>
```


## Commit Messages

Commit messages serve to describe the changes made on a high-level basis. Ensure that commit messages are informative, such as:
 *Resolved the bug where tabpanel 'summary' would not display until a driver was selected in login panel.*
      
- In this message, the implemented changes are sufficiently detailed for a user to be able to understand the specific code changes' intentions.

Overly detailed messages are not helpful and the cloud services do a better job at this. The following is too detailed: 
<em> Changed lines 114-121 to make use of more efficient code layout and formatting. Added spacing between logical operators on line 187 and 192. </em>

- More succinctly, this could read: <em> Formatted code according to style guide.  </em> 

Messages can be formatted with a subject and body, such as [here](https://chris.beams.io/posts/git-commit/#seven-rules), but rather commit frequently and keep changes small.

## Branches

Manage branches using an approach roughly based on [gitflow](https://nvie.com/posts/a-successful-git-branching-model/).
Every project should have the following branches:

* `master`
* `dev`

Feature branches should be made off `dev` and there should never have more than two *feature* branches active..  To create a new feature branch off of `dev`, first switch to `dev` branch.

```{r}
$ git checkout dev
```

Pull any changes from the cloud repository.

```{r}
$ git pull origin dev
```

Create the new branch off of `dev`.

```{r}
$ git checkout -b <new_feature_branch_name>
```

As a final step, push the new branch back to the cloud with and set up tracking.

```{r}
$ git push origin <new_feature_branch_name>
$ git branch --set-upstream-to=origin/<new_feature_branch_name> <new_feature_branch_name>
```

If you have forgotten to create a feature branch and have made changes to a non-feature branch, for instance `dev`, first stash your changes.

```{r}
$ git stash
```

Create a new branch as detailed above and check that you are on the new branch.

```{r}
$ git status
On branch <new_feature_branch_name>
```

Reapply your changes to the new branch.

```{r}
$ git stash pop
```

Commit your changes as detailed above.


## Merge Requests

Code should be thoroughly tested before a request is initiated, with tests conducted in an *empty* environment.

* In R, from RStudio terminal, clean all objects from the workspace.  

       ```{r}
       $ rm(list=list())
       ``` 

    + Restart your R session with `Ctrl`+`Shift`+`F10`. 
    
    
* In Python when using the VSCode IDE:

    + clear all variables by restarting the IPython kernel (top right of the interactive window).
    + Run the entire script by right-clicking and selection "Run All Cells".

Once the code has been tested, create a merge request on [Gitlab](https://gitlab.com/exegetic) or [Github](https://github.com/datawookie/www-exegetic-biz) by:

* Navigate to the merge request tab.
* Select the source branch to be merged and the destination branch, which is usually *develop*.
* Under the "Assignee", assign the merge request to the relevant project leader.

