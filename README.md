# Git Cheat-Sheet

## Git commands

### Display all branches
> `$ git show-branch`

git pull (update repo from origin)
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
