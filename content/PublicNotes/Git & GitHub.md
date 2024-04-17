---
title: Git & GitHub
Tags: Public
Aliases:
Date created: 2024-03-01 21:25
---
Git commands I forget too often

### Actions
[[GitHub Actions]]

### Repositories

#### Add Local Repo to GitHub
`git remote add <name> <remote url>`

#### Remove Directory from Repository, not Local
`git rm -r --cached <name> `

#### Merging Unrelated Histories
`git pull  --allow-unrelated-histories`

### Branches

#### Set Branch Tracking
`git branch -u <remote>/<branch>`
#### Auto Branch Tracking
`git config --global push.autoSetupRemote true`

#### Rename Branch
`git branch -m <new name>`

#### Move Uncommitted Changes to a New Branch
`git switch -c <new-branch>`

#### Get All Changes from Another Branch
```
git checkout clean_branch
git merge --squash changed_branch
```