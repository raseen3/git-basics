---
title: README.md
author: @raseen3
tags: ["abstract", "preface", "introduction"]
---
# git Basics {#title}

A review and cheat-sheet to study up on git

This Repository documents how to use each `git`-command in plain english and the different use cases and best practices.

## Table of Contents {#toc}

tbd

---

## Setting up ssh key

To generate an SSH key, first open your shell in the Home Directory.

Then ENTER:

```Bash
ssh-keygen -f ~/.ssh/keyforgithub -t ecdsa
```

and COPY the result of:

```bash
cat ~/.ssh/keyforgithub.pub
```

*you will have to have had git installed for this to work*

Then go to your code hosting platform of choice (i.e. GitHub, GitLab, etc.) and navigate to your account settings to where you can add a new SSH Key and PASTE what you just copied.

To add your git profile, add a file called config to your `/.ssh` directory:

```bash
touch ~/.ssh/config
```

and inside the file add the url your code is hosted on and on a new indented line the path to the ssh key
Example:

```git
Host github.com
    IdentityFile ~/.ssh/keyforgithub
```

To see if you key works ENTER the command:

```bash
ssh -T git@github.com
```

and if the output is something along the lines of

```bash
Hi _yourUsername_! You've successfully authenticated, but GitHub does not provide shell access
```

then you have successfully added you ssh key

## Bare Minimum

tbd

## Create a Repository

Create and/or navigate to inside the directory where you want your project to be stored inside then ENTER:

```git
git init
```

To be able to push to GitHub create a repository in GitHub and copy the repository link then ENTER:

```git
git remote add origin git@github.com:username/repository.git //or whatever what you copied was
```

and this will link your local repository to the one you are hosting online

Alternatively you can just do:

```git
git clone git@github.com:username/repository.git //or whatever what you copied was
```

## Common git commands

### git add [Option]

saves changes to local machine

### git add -A

Staged all files pending **addition**, **deletion**, and **modification**

### git commit [Option]

saves changes to local branch

### git commit -m "message"

Commits all the changes that have been staged

### git push [Options]

Saves/sends changes to the Remote branch hosted on GitHub

### git push -u origin working-branch-name

use this command the first time you push a change on a branch to set the origin of your changes

### git push remote --tags

Pushes local changes to the remote hosted branch along with all the tags

### git push origin --delete tag-name

deleted specified tag

### git pull

updates changes to what is saved in the Remote branch hosted on GitHub if the local branch is not up-to-date

### git status

tells you what branch you're on and the status of all files that have either been **added**, **deleted**, or **modified** between adds and commits and whether they are being staged

### git log

logs all the commits

### git diff [Options]

shows the difference between what you currently have and what is saved in the branch

### git diff file

Show changes between working directory and staging area.

### git diff --staged file

Shows any changes between the staging area and the repository.

## git config files

can set default commit message, git aliases, and specifer git user in the `.git` and `.gitconfig` file

can use `.gitignore` to ignore certain files
Example `.gitignore`:

```git
/logs/*
!logs/.gitkeep
/tmp
*.swp
```

Verify the .gitignore file exists in your project and ignore certain type
of files, such as all files in logs directory (excluding the .gitkeep file),
whole tmp directory and all files *.swp. File ignoring will work for the
directory (and children directories) where .gitignore file is placed.

## Conflict Resolution & File Directory Management

### git reset file

Revert your repository to a previous known working state.

### git revert

Create a new commit, reverting changes from the most recent commit.
It generates an inversion of changes.

### git rm file

Remove file from working directory and staging area

### get stash

Put current changes in your working direcotry into stash for later use

### git stash pop

Apply stored stash content into working directory, and clear stash

### git stash drop

Delete a specific stash from all your previous stashes

### git tag -a tag-name -m "tag message"

creates a tag named tag-name with a message tied to current commit (can specify commit)

## Branches

### git checkout branch-name

switches you to the specified branch (can also switch you to a specified tag if that is set up)

### git checkout -b new-Branch-Name

creates a copy of the current branch and switches to the new branch

### git merge branch-to-merge-from

merges specified branch into current working branch; assuming you are in the branch that you want to merge into (send all the changes to)

### Other Stuff

- [Git Source Control for the Impatient](https://www.youtube.com/watch?v=BaPexytJFTI&list=PLlcnQQJK8SUgfd_0XGzKveEjDGFbndmWr)

- [Engineer Man Git Playlist](https://www.youtube.com/playlist?list=PLlcnQQJK8SUjuzpRx0U-VEUzhmJD7vGbO)

- [Ihatetomatoes Git Tutorial Playlist](https://www.youtube.com/playlist?list=PLkEZWD8wbltmcZQaA0ism9k2E6MGRnHZ7)
