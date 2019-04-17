# GIT CHEAT SHEET

## CREATE

### Clone an existing repository

> `$ git clone [url]`

### Create a new local repository

> `$ git init`

## LOCAL CHANGES

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

## COMMIT HISTORY

### Show all commits, starting with newest

> `$ git log`

### Show changes over time for a specific file

> `$ git log -p <file>`

### Who changed what and when in \<file>

> `$ git blame <file>`

## BRANCHES & TAGS

### List all existing branches

> `$ git branch -av`

### Switch HEAD branch

> `$ git checkout <branch>`

### Create a new branch based on your current HEAD

> `$ git branch <new-branch>`
>
> `$ git checkout -b <new-branch>`

### Create a new tracking branch bases on a remote branch

> `$ git checkout -track <remote/branch>`

### Delete a local branch

> `$ git branch -d <branch>`

### Mark the current commit with a tag

> `$ git tag <tag-name>`

## UPDATE & PUBLISH

### List all existing branches

> `$ git remote -v`

### Show information about a remote

> `$ git remote show <remote>`

### Add new remote repository, named \<remote>

> `$ git remote add <shortname> <url>`

### Download all changes from \<remote>, but don't integrate into HEAD

> `$ git fetch <remote>`

### Download changes and directly merge/integrate into HEAD

> `$ git pull <remote> <branch>`

### Publish local changes on a remote

> `$ git push <remote> <branch>`

### Delete a branch on the remote

> `$ git branch -d <remote/branch>`

### Publish your tags

> `$ git push --tags`









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
