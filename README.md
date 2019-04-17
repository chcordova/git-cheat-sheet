# Git Cheat-Sheet

## Create

### Clone an existing repository
> `$ git clone [url]`

### Create a new local repository
> `$ git init`

## Local Changes

### Changed files in your working directory
> `$ git status`

### Changes to tracked files
> `$ git diff`

### Add all current changes to the next commit (all changes, without deletions and without new files)
> `$ git add -A`
>
> `$ git add .`
>
> `$ git add u`

### Add some changes in \<file> to the next commit
> `$ git add -p <file>`

### Commit all local changes in tracked files and add commit message
> `$ git commit -a`
> 
> `$ git commit -am [message]`

### Commit previusly staged changes
> `git commit`

### Change the last commmit
> `$ git commit -amend`

## Commit History

### Show all commits, starting with newest
> `$ git log`

### Show changes over time for a specific file
> `$ git log -p <file>`

### Who changed what and when in \<file>
> `$ git blame <file>`










### Display all branches
> `$ git show-branch`

### Display all branches
> `$ git show-branch`

### Update repo from origin
> `$ git pull`

Checkout:
* If you want to revert changes made to your working copy, do this: git checkout .
* git checkout -b develop~# develop
Clean / Reset:
* git reset
* git checkout .
* git clean -fdx 
Add:
* git add -A “stages All”
* git add . “stages new and modified, without deleted”
* git add -u “stages modified and deleted, without new”
Commit:
* This command will add and commit all the modified files, but not newly created files: $ git commit -am  "<commit message>"
* One-liner to stage ALL files (modified, deleted, and new) and commit with comment: $ git add --all && git commit -m "comment"
Push:
* git push origin develop
Git Flow:
* git checkout develop
* git pull
* git flow init
* git flow feature start *feature_name*
* git flow feature publish *feature_name*
* git flow feature finish *feature_name*
