# Git & GitHub Collaborative Documentation

## 1. Introduction

### What is Git?

Git is a distributed version control system used to track changes in files and source code. It helps developers maintain project history, compare changes, and collaborate with other developers.

### What is GitHub?

GitHub is an online platform that hosts Git repositories. It allows developers to share code, collaborate on projects, and review changes.

### Difference Between Git and GitHub

- **Git:** Tracks changes to project files and records their history.
- **GitHub:** Hosts Git repositories online and supports collaboration.

## 2. Essential Git Commands

This section explains common Git commands, their syntax, practical examples, and real-world uses.

### 2.1 Configure Git

**Purpose:** Set the name and email address recorded in your commits.

**Commands:**

    git config --global user.name "Your Name"
    git config --global user.email "your@email.com"

**Example:**

    git config --global user.name "Emerance Himbazwe"
    git config --global user.email "your-email@example.com"

Replace the example email with the email associated with your GitHub account.

**Use case:** Configure your identity before making commits.

### 2.2 Initialize a Repository

**Command:**

    git init

**Explanation:** Initializes a new Git repository in the current directory.

**Use case:** Start tracking changes in a new project.

### 2.3 Clone a Repository

**Command:**

    git clone https://github.com/USERNAME/REPOSITORY.git

**Explanation:** Downloads a copy of a remote repository to your computer.

**Use case:** Get a copy of an existing team project to work on locally.

### 2.4 Check Repository Status

**Command:**

    git status

**Explanation:** Displays changed, staged, and untracked files.

**Use case:** Check which files need to be staged or committed.

### 2.5 Stage Changes

**Commands:**

    git add README.md
    git add .

**Explanation:** Adds changes to the staging area before committing.

**Use case:** Select the changes you want to include in the next commit.

### 2.6 Commit Changes

**Command:**

    git commit -m "Add essential Git commands"

**Explanation:** Records staged changes in the local repository.

**Use case:** Save a meaningful unit of work with a descriptive commit message.

### 2.7 View Commit History

**Commands:**

    git log
    git log --oneline

**Explanation:** Displays the history of commits in the repository.

**Use case:** Review previous changes and identify who made each commit.


## 3. Collaborative Contributions

This documentation is a collaborative project. Each team member will contribute a separate section covering different Git commands, examples, and practical use cases.

- **Emerance Himbazwe:** Introduction and essential Git commands.
- **Roxane:** Branching, merging, merge conflict resolution, and collaboration.
- **Kenia:** Remote repositories, synchronization, and advanced Git commands.
## 4. Branching and Collaboration

Branches let you work on a feature, a bug fix, or an experiment without touching the stable code. Each branch is an independent line of development, and you merge it back when the work is ready. This is the foundation of teamwork in Git.

### 4.1 git branch

`git branch` lists, creates, renames, and deletes branches. It does **not** move you onto a branch; use `git switch` for that.

**Syntax**

```bash
git branch                      # list local branches (* marks the current one)
git branch -a                   # list local and remote branches
git branch <name>               # create a new branch at the current commit
git branch -m <old> <new>       # rename a branch
git branch -d <name>            # delete a branch that is already merged
git branch -D <name>            # force-delete a branch (even if unmerged)
```

**Example**

```bash
git branch feature/login
git branch
#   feature/login
# * main
```

**Use case:** Before starting any new task, create a branch for it so `main` always stays clean and working.

**Naming tip:** use short, descriptive names with a prefix, such as `feature/login`, `fix/navbar-bug`, or `docs/git-guide`.

### 4.2 git switch

`git switch` moves you to another branch. It was introduced in Git 2.23 as a clearer alternative to `git checkout`, which does many unrelated things.

**Syntax**

```bash
git switch <branch>             # move to an existing branch
git switch -c <new-branch>      # create a branch and move to it in one step
git switch -                    # go back to the previous branch
```

**Example**

```bash
git switch -c feature/login     # create and move to feature/login
# ... edit files ...
git add .
git commit -m "feat: add login form"
git switch main                 # go back to main
```

When you switch, the files in your working folder change to match that branch.

**Older equivalent:** `git checkout <branch>` and `git checkout -b <new-branch>` do the same thing and you will still see them in many tutorials.

**Use case:** Quickly jump between your feature work and `main` to compare behavior or pull the latest changes.

### 4.3 git merge

`git merge` combines the history of one branch into the branch you are currently on.

**Syntax**

```bash
git merge <branch>              # merge <branch> into the current branch
git merge --no-ff <branch>      # always create a merge commit
git merge --abort               # cancel a merge that is in progress
```

**Step-by-step example**

```bash
git switch main                 # 1. go to the branch that should receive the changes
git pull origin main            # 2. make sure it is up to date
git merge feature/login         # 3. bring in the feature branch
git branch -d feature/login     # 4. delete the branch once it is merged
```

**Two kinds of merge**

| Type | When it happens | Result |
|------|-----------------|--------|
| **Fast-forward** | `main` has no new commits since the branch was created | Git just moves the `main` pointer forward; no merge commit |
| **Three-way merge** | Both branches have new commits | Git creates a new merge commit combining both histories |

**Use case:** After a feature is finished and reviewed, merge it into `main` so the whole team gets it.

### 4.4 Merge Conflicts and How to Resolve Them

A **merge conflict** happens when two branches change the same lines of the same file (or one branch deletes a file the other edited) and Git cannot decide which version to keep. Git stops the merge and asks you to resolve it.

**Step 1: Trigger and spot the conflict**

```bash
git merge feature/login
# Auto-merging index.html
# CONFLICT (content): Merge conflict in index.html
# Automatic merge failed; fix conflicts and then commit the result.
```

```bash
git status                      # lists files under "Unmerged paths"
```

**Step 2: Open the file and read the markers**

```
<<<<<<< HEAD
<h1>Welcome to our site</h1>
=======
<h1>Welcome to the Student Portal</h1>
>>>>>>> feature/login
```

- Between `<<<<<<< HEAD` and `=======` is **your current branch's** version.
- Between `=======` and `>>>>>>> feature/login` is the **incoming branch's** version.

**Step 3: Edit the file to the final version you want**

Keep one side, the other, or a combination, and **delete all three marker lines**:

```
<h1>Welcome to the Student Portal</h1>
```

**Step 4: Mark it resolved and finish the merge**

```bash
git add index.html
git commit                      # Git pre-fills a merge message; save it
```

**Other useful commands**

```bash
git merge --abort               # give up and return to the state before the merge
git checkout --ours <file>      # keep your version of a conflicted file
git checkout --theirs <file>    # keep the incoming version of a conflicted file
git diff --name-only --diff-filter=U   # list the files still in conflict
```

**How to avoid conflicts**

- Pull from `main` often so your branch does not drift far behind.
- Keep branches small and short-lived.
- Talk with teammates before editing the same file.

### 4.5 git stash

`git stash` temporarily shelves your uncommitted changes so you can switch tasks with a clean working directory, then bring the changes back later.

**Syntax**

```bash
git stash                       # stash tracked, modified files
git stash push -m "message"     # stash with a descriptive name
git stash -u                    # also stash untracked (new) files
git stash list                  # show all saved stashes
git stash pop                   # re-apply the latest stash and remove it from the list
git stash apply stash@{1}       # re-apply a specific stash and keep it in the list
git stash drop stash@{0}        # delete a specific stash
git stash clear                 # delete all stashes
```

**Example**

```bash
# You are halfway through a feature when a teammate reports an urgent bug
git stash push -m "half-done login form"
git switch main
git switch -c fix/urgent-bug
# ... fix the bug, commit, push ...
git switch feature/login
git stash pop                   # your unfinished work comes back
```

**Use case:** Git refuses to switch branches when your uncommitted changes would be overwritten. Stash them, switch, and restore them afterwards.

### 4.6 Real-World Teamwork Examples

**Example 1: Feature-branch workflow (the everyday routine)**

```bash
git switch main
git pull origin main                    # start from the latest code
git switch -c feature/contact-page      # one branch per task
# ... write code ...
git add .
git commit -m "feat: add contact page"
git push -u origin feature/contact-page # publish your branch
```

Then on GitHub: open a **Pull Request**, ask a teammate to review it, and merge it into `main` once approved. Finally, clean up:

```bash
git switch main
git pull origin main
git branch -d feature/contact-page
```

**Example 2: Two teammates, same file, one conflict**

1. Two teammates both start from `main` and create their own branches.
2. Both edit the same line in `README.md`.
3. The first teammate's pull request is merged.
4. The second teammate updates their branch to catch up:
   ```bash
   git switch docs/branching
   git pull origin main            # conflict appears in README.md
   ```
5. They open the file, keep the correct content, remove the markers, then:
   ```bash
   git add README.md
   git commit
   git push
   ```
6. Their pull request now merges cleanly.

**Example 3: Interrupted by an urgent bug**

Use `git stash` (see 4.5) to shelve your unfinished work, fix the bug on a separate branch, and come back with `git stash pop`.

**Suggested team rules**

- Never commit directly to `main`; always use a branch and a pull request.
- One branch per feature or fix, with a clear name.
- Pull before you push, and pull `main` into your branch regularly.
- Write meaningful commit messages (for example `fix: correct footer link`).

### 4.7 Quick Reference

| Task | Command |
|------|---------|
| List branches | `git branch` |
| Create a branch | `git branch <name>` |
| Create and switch | `git switch -c <name>` |
| Switch branch | `git switch <name>` |
| Merge a branch | `git merge <name>` |
| Abort a merge | `git merge --abort` |
| Delete a merged branch | `git branch -d <name>` |
| Stash changes | `git stash push -m "msg"` |
| Restore stash | `git stash pop` |