# Git Commands



What is Git: a version control system which track changes in a set of files

Working Directory: changes on disk
Staging Area: changes ready to commit
Committed Code: code in a commit

git init: initializes directory as a Git repository

git clone [url]: retrieve a repo from a hosted location via URL

git status: shows modified files

git add [file]: stage (area that represents "to be committed" a file). The opposite of this is git reset [file] (unstages a file)

git diff: diff of what is changed but not staged, or diff between commits, or files

git aliases: by changin ~/.gitconfig

Branches: separate workspace
Master: default branch which represents stable version of code, therefore we don't want to experiment on this branch
Creating isolated environment to try a new feature is the concept of branching which can be merged later

Creating branch copies the code at a certain point, and then once we are happy with it, it can be merged into the master branch. If we don't like how it turns out, the branch can be deleted.

git branch [name]: creates new branch with name

git branch: shows all the branches * appears next to the current branch (ie. master)

git checkout [branch-name]: changing current branch to branch-name

git checkout -b [branch-name]: combines step git branch [name] and git checkout [branch-name]

git log: shows commit history

git stash: takes uncommitted changes and saves them away, reverting them from working directory. Stash is a stack data structure.

git stash pop: write to working directory from the the top of the stash stack

git rm [file]: removes the file

git fetch: 'safe' version, will download remote content but not change the working directory

git pull: 'aggresive' version, downloads remote content (git fetch) and immediately executes git merge which affects the working directory

git remote add origin [url]: creates remote reference to the server

upstream: original repo

origin: your fork

git pull from origin would mean you want the latest changes from your fork (ie. you made edits on multiple computers or with teammates)

git pull from upstream would mean you wnat the latest changes from the original repo (ie. multiple contributors)

git revert: remove all the changes a single commit made to your source code repository (typically used in a public branch/larger team)
git revert --no-commit f414f31..HEAD

git reset --hard [commit]: undoes changes (used in your own private branch and not a public branch). deletes commits after the one being newly pointed to.

git rebase: apply any commits of current branch ahead of specified one, preventing non linear commit trees

How to revert to a previous commit:
Option 1: 
Push a new commit which reverts to a previous commit. Thus there will be an original commit and a new identical one. The right choice for public or shared branches, as it prevents deletion of commit which other people may be dependent on.
git revert
Option 2:
Delete pushed commit. 
git reset

--


Using Https:

Using ssh:
git clone git@github.com:owner/repo.git
