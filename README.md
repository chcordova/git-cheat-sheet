# 🚀 Git Quick Guide: Advanced Edition for Professionals

> Your essential co-pilot in the Git universe. This isn't your typical cheat sheet; it's a modernized and enhanced guide for you to master Git like a pro. From fundamental day-to-day commands to the most effective branching strategies like Trunk-Based Development and Gitflow. Forget about forgotten commands and existential doubts about `rebase` vs. `merge`. With clear explanations, updated best practices, and pro tips, this guide will turn you into a version control master. Get your terminal ready and *commit* with confidence!

---

**Table of Contents:**

* [❓ Help & Documentation](#help--documentation)
* [🌱 Creation & Initialization](#creation--initialization)
* [✍️ Local Changes](#local-changes)
* [📜 Commit History](#commit-history)
* [🌿 Branches & Tags](#branches--tags)
* [🔄 Updating & Publishing (Remotes)](#updating--publishing-remotes)
* [🤝 Merging & Rebasing](#merging--rebasing)
* [↩️ Undoing Changes](#undoing-changes)
* [🌊 Branching Strategies: Advice](#branching-strategies-advice)
    * [🌳 Trunk-Based Development (TBD)](#trunk-based-development-tbd)
    * [🌊 Gitflow](#gitflow)
    * [💡 Other Strategies (Brief Mention)](#other-strategies-brief-mention)
* [❌ Extras (Use With Caution!)](#extras-use-with-caution)

---

## ❓ Help & Documentation

### `git help <command>`
Get detailed help directly from the command line for any Git command.
*Example:* `git help commit`

---

## 🌱 Creation & Initialization

### `git clone <repository_url>`
Clone an existing repository to your local machine.
* **Pro Tip:** For very large repositories, consider `git clone --depth 1 <repository_url>` to clone only the most recent history.

### `git init`
Initialize a new Git repository in the current directory.
* **Best Practice (2024+):** To set `main` as the default branch from the start: `git init -b main`

---

## ✍️ Local Changes

### `git status`
Shows the status of files in your working directory and staging area.
* `git status -s` or `git status --short`: Shows a concise summary.

### `git diff`
Shows the differences between modified files and their last version in the repository (HEAD).
* `git diff --staged` or `git diff --cached`: Shows the differences of files already in the staging area against the last commit.
* `git diff <branch_or_commit_name>`: Shows the differences between your current branch and another branch or commit.

### `git add <file_or_directory>`
Adds changes from specific files or a directory to the staging area for the next commit.
* `git add .`: Adds all new and modified files (excluding deleted by default) from the current directory downwards.
* `git add -A` or `git add --all`: Adds all changes (new, modified, deleted) in the entire repository.
* `git add -u`: Adds all modified and deleted files (not new ones) in the entire repository.
* `git add -p` or `git add --patch`: Allows you to interactively add portions (hunks) of changes from a file. Very useful for atomic commits!

### `git commit -m "Commit message"`
Saves the changes from the staging area to the local repository with a descriptive message.
* **Best Practice:** Write clear and concise commit messages. Consider using [Conventional Commits](https://www.conventionalcommits.org/) for standardization.
* `git commit`: Opens the configured text editor to write a more detailed message.

### `git commit --amend`
Modifies the last commit. Useful for correcting the message or adding forgotten changes.
* `git commit --amend --no-edit`: Modifies the last commit with the current changes in staging, but without changing the commit message.
* ⚠️ **Important:** **Never use `git commit --amend` on commits that you have already pushed to a shared remote repository**, as it rewrites history.

---

## 📜 Commit History

### `git log`
Shows the commit history, starting with the most recent.
* `git log --oneline`: Shows a summarized version of the history.
* `git log --graph --decorate --all --oneline`: A graphic and compact view of all branches.
* `git log -p <file>`: Shows the changes introduced in a specific file over time.
* `git log --author="<author_name>"`: Filters commits by author.
* `git log --grep="<pattern_in_message>"`: Searches for commits whose messages contain a specific pattern.

### `git blame <file>`
Shows who modified what line of a file and in which commit.
* `git blame -L <start_line>,<end_line> <file>`: Limits the `blame` to a range of lines.

---

## 🌿 Branches & Tags

### `git branch`
Lists all local branches.
* `git branch -r`: Lists remote-tracking branches that your local repository knows.
* `git branch -a`: Lists all branches (local and remote-tracking).
* `git branch -vv`: Shows local branches and which remote branch they are tracking, along with the last commit.

### `git switch <branch_name>`
Switches to an existing branch. (Preferred over `git checkout <branch_name>` for switching branches).
* **Best Practice:** Use `git switch` to change branches and `git restore` to discard changes.

### `git switch -c <new_branch_name>`
Creates a new branch and switches to it. (Preferred over `git checkout -b <new_branch_name>`).
* `git branch <new_branch_name>`: Creates a new branch but does not switch to it.

### `git switch -c <local_branch_name> <remote_name/branch_name>`
Creates a new local branch that tracks a remote branch.
*Example:* `git switch -c feature/login origin/feature/login`
* **Pro Tip:** If the local branch name is the same as the remote one (e.g., `feature/login`), you can often just do `git switch feature/login`, and Git will infer tracking if a remote branch with that name exists and a local one doesn't.

### `git branch -d <branch_name>`
Deletes a local branch. Only works if the branch has been merged.
* `git branch -D <branch_name>`: Forces the deletion of a local branch, even if it hasn't been merged. Use with care!

### `git tag <tag_name>`
Marks the current commit with a lightweight tag.
* `git tag -a <tag_name> -m "Tag message"`: Creates an annotated tag, which is the recommended practice as it includes metadata like author, date, and message.
* `git tag`: Lists all tags.
* `git show <tag_name>`: Shows information about a specific tag.

---

## 🔄 Updating & Publishing (Remotes)

### `git remote -v`
Lists all configured remote repositories with their URLs.

### `git remote show <remote_name>`
Shows detailed information about a remote repository (e.g., `origin`).

### `git remote add <short_name> <repository_url>`
Adds a new remote repository.
*Example:* `git remote add upstream https://github.com/other_user/project.git`

### `git fetch <remote_name>`
Downloads all changes (commits, branches, tags) from the remote repository, but **does not integrate them** into your local HEAD or working directory. It updates your remote-tracking branches (e.g., `origin/main`).
* `git fetch --all`: Downloads from all remotes.
* `git fetch --prune`: Removes remote-tracking branches that no longer exist on the remote.

### `git pull <remote_name> <branch_name>`
Downloads changes from the remote and automatically merges or rebases the remote branch into your current local branch. It's equivalent to `git fetch` followed by `git merge <remote_name>/<branch_name>` (or `git rebase`).
* **Best Practice:** `git pull --rebase <remote_name> <branch_name>` is often preferred to maintain a linear history, especially in collaborative workflows.

### `git push <remote_name> <local_branch_name>:<remote_branch_name>`
Uploads your local changes (commits) to a remote repository.
* `git push <remote_name> <branch_name>`: Shorthand if the local and remote branch names are the same.
* `git push -u <remote_name> <branch_name>` or `git push --set-upstream <remote_name> <branch_name>`: Used the first time you push a new branch to establish the tracking relationship between your local and remote branch. Afterwards, you only need `git push`.
* `git push <remote_name> --delete <branch_name>`: Deletes a branch on the remote repository. (Older alternative: `git push <remote_name> :<branch_name>`)
* `git push --tags`: Uploads all your local tags to the remote.
* `git push <remote_name> <tag_name>`: Uploads a specific tag.

---

## 🤝 Merging & Rebasing

### `git merge <branch_name>`
Merges changes from `<branch_name>` into your current branch (HEAD). Creates a merge commit if there's a divergence (not a fast-forward).
* `git merge --no-ff <branch_name>`: Forces the creation of a merge commit even if a fast-forward is possible. Useful for maintaining an explicit record of feature branch merges.
* `git merge --squash <branch_name>`: Combines all commits from `<branch_name>` into a single commit on your current branch, without recording the history of the merged branch. You then need to `git commit`.

### `git rebase <base_branch>`
Reapplies commits from your current branch onto the tip of `<base_branch>`. This results in a linear history.
* ⚠️ **Important:** **Never use `git rebase` on commits that you have already pushed to a shared remote repository**, as it rewrites history. It's safe for local branches before sharing them.
* `git rebase -i <base_commit_or_branch>` or `git rebase --interactive <base_commit_or_branch>`: Allows you to edit, reorder, combine (squash), or delete commits interactively. Very powerful for cleaning up the history of a feature branch before merging it.

### `git rebase --abort`
Cancels a rebase in progress and returns the branch to its previous state.

### `git rebase --continue`
Continues a rebase after resolving conflicts.

### `git rebase --skip`
Skips the current commit during a rebase and continues with the next one.

### Conflict Resolution (During Merge or Rebase)
1.  Git will inform you about files with conflicts.
2.  Open the conflicting files in your editor. Look for markers `<<<<<<<`, `=======`, `>>>>>>>`.
3.  Edit the files to resolve the differences. Remove the Git markers.
4.  `git add <resolved_file>`: Marks the file as resolved.
5.  If you are in a `merge`, do `git commit` (or `git merge --continue`).
6.  If you are in a `rebase`, do `git rebase --continue`.

### `git mergetool`
Uses a configured graphical tool to resolve merge conflicts.

---

## ↩️ Undoing Changes

### `git restore <file>`
Discards changes in the working directory for a specific file, restoring it to how it is in the staging area, or in the last commit (HEAD) if not in staging.
* **Best Practice:** Preferred over `git checkout -- <file>`.

### `git restore --staged <file>`
Removes a file from the staging area, but keeps the changes in the working directory.
* **Best Practice:** Preferred over `git reset HEAD <file>`.

### `git clean -fdx`
Removes untracked files and directories.
* `-f`: Force.
* `-d`: Include directories.
* `-x`: Include files ignored by `.gitignore`.
* ⚠️ **Dangerous:** Use with extreme caution. `git clean -fdxn` (or `--dry-run`) shows what would be deleted without actually doing it.

### `git revert <commit_hash>`
Creates a **new commit** that reverts the changes introduced by the specified `<commit_hash>`. It's the safe way to undo commits that have already been shared.

### `git reset <options> <commit_hash>`
Moves the HEAD pointer (and optionally the index and working directory) to a previous commit.
* `git reset --soft <commit_hash>`: Moves HEAD to `<commit_hash>`. Changes from undone commits are left in the staging area.
* `git reset --mixed <commit_hash>` (or simply `git reset <commit_hash>`): Moves HEAD to `<commit_hash>` and resets the staging area. Changes from undone commits are left in the working directory as unstaged changes. **This is the default mode.**
* `git reset --hard <commit_hash>`: Moves HEAD to `<commit_hash>`, resets the staging area and the working directory. ⚠️ **Dangerous:** All uncommitted local changes and changes from undone commits will be lost.
* ⚠️ **Important:** Avoid `git reset` (especially `--hard`) on commits that you have already pushed to a shared remote, as it rewrites history.

---

## 🌊 Branching Strategies: Advice

There are several popular branching strategies. The two best known are Trunk-Based Development and Gitflow. Others like GitHub Flow and GitLab Flow also exist.

### 🌳 Trunk-Based Development (TBD)

**Concept:** All developers integrate their changes directly and frequently (at least once a day) to a single main branch called `main` (or `trunk`). Feature branches, if used, are very short-lived (days or even hours) and merged quickly. It relies heavily on robust automated tests, Continuous Integration (CI), and Feature Flags to manage the visibility of incomplete functionalities.

**Key Commands and Typical Workflow (with short-lived feature branches):**

1.  **Sync with the trunk:**
    `git switch main`
    `git pull --rebase origin main` (Maintain linear history)
2.  **Create a short-lived feature branch (if needed):**
    `git switch -c feature/short-descriptive-name main`
3.  **Work and make local commits:**
    `git add .`
    `git commit -m "feat: implement X"`
4.  **Keep the feature branch updated (optional, if it lasts more than a few hours):**
    `git fetch origin`
    `git rebase origin/main` (Rebase your feature onto the latest changes from main)
    (Resolve conflicts if any)
5.  **When the feature is ready (and tested):**
    `git switch main`
    `git merge --squash feature/short-descriptive-name` (Squash to keep `main` history clean)
    `git commit -m "feat: Implemented X functionality (squashed #123)"` (Message can reference the task)
    `git branch -d feature/short-descriptive-name` (Delete local branch)
6.  **Push to `main`:**
    `git push origin main`

**TBD Alternative (no feature branches, directly to `main`):**
For very small changes and with very robust CI/CD.
1.  `git switch main`
2.  `git pull --rebase origin main`
3.  Make changes, `git add .`, `git commit -m "fix: correct Y error"`
4.  `git push origin main` (Tests must pass in CI before this is deployed!)

**TBD Advantages:**
* Real continuous integration.
* Fewer complex merge conflicts.
* Fast and frequent deployments.
* Quick feedback.

**TBD Disadvantages:**
* Requires a mature engineering culture and discipline.
* Critical dependence on Feature Flags and automated tests.

### 🌊 Gitflow

**Concept:** A more structured branching model with long-lived branches and specific roles:
* `main` (or `master`): Contains stable production code. Only merged from `release` or `hotfix`.
* `develop`: Main development branch, integrates completed features. It's the base for `release` branches.
* `feature/*`: Branches for new functionalities. Created from `develop` and merged back into `develop`.
* `release/*`: Branches to prepare a new production release. Created from `develop`. Allow for last-minute fixes and metadata preparation. Merged into `main` and `develop`.
* `hotfix/*`: Branches for critical production fixes. Created from `main` and merged into `main` and `develop`.

**Key Commands (using the `git-flow` extension or manually):**
The `git flow-avh` extension simplifies this, but the manual commands are:

* **Initialize Repository (with `git-flow` extension):**
    `git flow init -d` (Accepts default values)

* **Start a Feature (from `develop`):**
    * With `git-flow`: `git flow feature start FEATURE_NAME`
    * Manually:
        `git switch develop`
        `git pull origin develop`
        `git switch -c feature/FEATURE_NAME develop`

* **Finish a Feature (merge into `develop`):**
    * With `git-flow`: `git flow feature finish FEATURE_NAME` (Merges to `develop` and deletes the branch)
    * Manually:
        `git switch develop`
        `git pull origin develop`
        `git merge --no-ff feature/FEATURE_NAME`
        `git branch -d feature/FEATURE_NAME`
        `git push origin develop`

* **Start a Release (from `develop`):**
    * With `git-flow`: `git flow release start VERSION` (e.g., `1.0.0`)
    * Manually:
        `git switch develop`
        `git pull origin develop`
        `git switch -c release/VERSION develop`

* **Finish a Release (merge into `main` and `develop`, tag):**
    * With `git-flow`: `git flow release finish VERSION` (Asks for GPG key if configured for signing tags)
    * Manually:
        `git switch main`
        `git pull origin main`
        `git merge --no-ff release/VERSION`
        `git tag -a VERSION -m "Release VERSION"` (or just `VERSION`)
        `git push origin main --tags`
        `git switch develop`
        `git pull origin develop`
        `git merge --no-ff release/VERSION`
        `git push origin develop`
        `git branch -d release/VERSION`
        `git push origin --delete release/VERSION` (if the release branch was pushed)

* **Start a Hotfix (from `main`):**
    * With `git-flow`: `git flow hotfix start HOTFIX_VERSION` (e.g., `1.0.1`)
    * Manually:
        `git switch main`
        `git pull origin main`
        `git switch -c hotfix/HOTFIX_VERSION main`

* **Finish a Hotfix (merge into `main` and `develop`, tag):**
    * With `git-flow`: `git flow hotfix finish HOTFIX_VERSION`
    * Manually: Similar to finishing a release (merge to `main`, tag, merge to `develop`, delete branch).

**Gitflow Advantages:**
* Very structured, clear for large teams or projects with defined release cycles.
* Good for managing multiple versions in production.

**Gitflow Disadvantages:**
* Can be complex and ceremonial for small teams or projects with continuous deployment.
* The `develop` branch can diverge significantly from `main` if releases are infrequent.

### 💡 Other Strategies (Brief Mention)

* **GitHub Flow:** Very simple. `main` is always deployable. Features are developed in branches (`feature/*`) created from `main`. Pull Requests (PRs) are opened for discussion and review. Once approved and tests are OK, it's merged into `main` and deployed. Ideal for CI/CD.
* **GitLab Flow:** Similar to GitHub Flow but can be more prescriptive about environment branches (e.g., `staging`, `production`) or release branches if needed, offering a middle ground between GitHub Flow's simplicity and Gitflow's structure.

**Which to choose?**
* **Trunk-Based Development:** Ideal for teams seeking high velocity, mature CI/CD, and can manage complexity with feature flags.
* **Gitflow:** Good for projects with longer, defined release cycles, or when you need to maintain multiple supported production versions.
* **GitHub/GitLab Flow:** Excellent options for most modern web projects practicing CI/CD, offering a good balance between simplicity and structure.

---

## ❌ Extras (Use With Caution!)

### `rm -rf .git`
Deletes the `.git` directory from the repository. This **deletes all Git history** and turns the project into a normal, unversioned directory.
* ⚠️ **Use only if you know exactly what you are doing and want to permanently unlink the project from Git!** There is no confirmation.

---
