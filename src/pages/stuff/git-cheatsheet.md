---
layout: "../../layouts/Page.astro"
title: "git Cheatsheet"
---

## View list of commits

When running `git pull` you might get ... `Updating f0d3463..4262b6b`

### Get list of one-liners

```bash
git log --oneline f0d3463..4262b6b
```

### Get detailed summary

```bash
git log -p f0d3463..4262b6b
```

### View specific file changes

```bash
git diff f0d3463..4262b6b
```

### List files changed

```bash
git diff --name-only f0d3463..4262b6b
```

### Summary of changes

```bash
git diff --stat f0d3463..4262b6b
```

## Misc

### How to edit the last commit message

```bash
git commit --amend -m "New commit message"
```

## Branches

### Create and checkout a new branch

```bash
git checkout -b <branch-name>
```

#### Create and checkout new branch from specific branch

```bash
git checkout -b <new-branch-name> <existing-branch-name>
```

#### Only create branch but don't switch

```bash
git branch <new-branch-name> <existing-branch-name>
```

### Copy specific file from another branch

```bash
git checkout <other-branch-name> -- path/to/file
```

### Diff file against same file in other branch

```bash
git diff <other-branch-name> -- path/to/file
```

### Incorporate updates to `main` and merge back into `main`

```bash
git pull origin main
```

Resolve any files if necessary, then stage:

```bash
git add . \
git commit -m "Merge main into feature branch"
```

Check out main and merge feature branch into it:

```bash
git checkout main \
git merge <branch-name>
```

Push to remote:

```bash
git push origin main
```

### Remove local branches deleted on the remote

#### Step 1: Update remote tracking info:

Done by pruning (you can also use `--prune`)

```bash
git fetch -p
```

#### Step 2: Check and delete

Check local branches tracking deleted remote branches:

```bash
git branch -vv
```

Look for branches that show `[origin/branch-name: gone]`

Delete those with:

```bash
git branch -d <branch-name>
```
