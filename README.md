# GIT CHEAT SHEET

## HELP & DOCUMENTATION

### Get help on the command line

> `$ git help <command>`

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

## MERGE & REBASE

### Merge \<branch> into your current HEAD

> `$ git merge <branch>`

### Rebase your current HEAD onto \<branch> (Don't rebase publish commits)

> `$ git rebase <branch>`

### Abort a rebase

> `$ git rebase --abort`

### Use your configured merge tool to solve conflicts

> `$ git mergetool`

### Use your editor to manually solve conflicts and (after resolving) mark file as resolved

> `$ git add <resolved-file>`
>
> `$ git rm <resolved-file>`

## UNDO

### Discard all local changes in yout working directory

> `$ git reset --hard HEAD`
>
> `$ git reset`
>
> `$ git checkout .`
>
> `$ git clean -fdx`
>
> `$ git checkout -b develop~# develop`

### Discard local changes in a specific file

> `$ git checkout HEAD <file>`

### Revert a commit (by producing a new commit with contrary changes)

> `$ git revert <commit>`

### Reset your HEAD pointer to a previous commit and discard all changes since then, perserve all changes as unstaged changes and preserve uncommitted local changes

> `$ git reset --hard <commit>`
>
> `$ git reset <commit>`
>
> `$ git reset --keep <commit>`

## GIT FLOW

### Init git flow

> `$ git flow init`

### Start git flow feature

> `$ git flow feature start [feature-name]`

### Publish git flow feature

> `$ git flow feature publish [feature-name]`

### Finish git flow feature

> `$ git flow feature finish [feature-name]`

## Extra

### Delete .git folder

> `$ rm -rf .git`
