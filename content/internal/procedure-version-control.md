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
- You should never have more than two feature branches active.

### Merge/Pull Requests Requests

- Code should be thoroughly tested before a request is initiated.
    - Tests should be conducted with an *empty* environment.