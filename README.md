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

```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
```

**Example:**

```bash
git config --global user.name "Emerance Himbazwe"
git config --global user.email "your-email@example.com"
```

Replace the example email with the email associated with your GitHub account.

**Use case:** Configure your identity before making commits.

### 2.2 Initialize a Repository

```bash
git init
```

Initializes a new Git repository in the current directory.

**Use case:** Start tracking changes in a new project.

### 2.3 Clone a Repository

```bash
git clone https://github.com/USERNAME/REPOSITORY.git
```

Downloads a copy of a remote repository to your computer.

**Use case:** Get a copy of an existing team project to work on locally.

### 2.4 Check Repository Status

```bash
git status
```

Displays changed, staged, and untracked files.

**Use case:** Check which files need to be staged or committed.

### 2.5 Stage Changes

```bash
git add README.md
git add .
```

Adds changes to the staging area before committing.

**Use case:** Select the changes you want to include in the next commit.

### 2.6 Commit Changes

```bash
git commit -m "Add essential Git commands"
```

Records staged changes in the local repository.

**Use case:** Save a meaningful unit of work with a descriptive commit message.

### 2.7 View Commit History

```bash
git log
git log --oneline
```

Displays the history of commits in the repository.

**Use case:** Review previous changes and identify who made each commit.

## 3. Collaborative Contributions

This documentation is a collaborative project. Each team member contributes a separate section covering different Git commands, examples, and practical use cases.

- **Emerance Himbazwe:** Introduction and essential Git commands.
- **Roxane:** Branching, merging, merge conflict resolution, and collaboration.
- **Kenia:** Remote repositories, synchronization, and advanced Git commands.

## 4. Remote Repositories and Advanced Git Commands — Kenia

This section explains how to connect to remote repositories, synchronize changes between a local computer and GitHub, and manage commit history safely.

### 4.1 Git Remote

**Purpose:** The `git remote` command manages connections to remote repositories, such as repositories hosted on GitHub.

**Commands:**

```bash
git remote
git remote -v
git remote add origin https://github.com/USERNAME/REPOSITORY.git
git remote get-url origin
```

**Explanation:**

- `git remote` lists configured remote names.
- `git remote -v` displays remote names and their URLs.
- `git remote add origin URL` connects the local repository to a remote repository named `origin`.
- `git remote get-url origin` displays the URL of the remote named `origin`.

**Practical example:**

```bash
git remote -v
```

This checks which remote repository your local project is connected to.

**Use case:** Check that your local repository points to the correct team repository before pushing changes.

**Common mistake:** Adding `origin` when it already exists may produce an error. Check existing remotes with `git remote -v` first.

### 4.2 Git Fetch

**Purpose:** The `git fetch` command downloads new commits and updated information from a remote repository without merging those changes into your current branch.

**Syntax:**

```bash
git fetch origin
```

**Practical example:**

```bash
git fetch origin
git log --oneline HEAD..origin/main
```

The first command downloads updates from `origin`. The second displays commits on `origin/main` that are not reachable from your current `HEAD`, assuming `origin/main` exists.

**Use case:** Check your teammates' latest changes before integrating them into your branch.

**Common mistake:** Thinking that `git fetch` automatically updates your working files. It downloads information but does not merge the changes into your current branch.

### 4.3 Git Pull

**Purpose:** The `git pull` command downloads changes from a remote repository and integrates them into the current branch.

**Syntax:**

```bash
git pull origin main
```

**Practical example:**

```bash
git switch main
git pull origin main
```

These commands switch to the local `main` branch and integrate updates from the remote `main` branch.

**Use case:** Get the latest version of a shared project before starting new work.

**Common mistakes:**

- Pulling from the wrong branch.
- Having uncommitted changes that conflict with incoming changes.
- Confusing `git pull` with `git fetch`.

**Tip:** Run `git status` before pulling. Commit or safely stash important changes first.

### 4.4 Git Push

**Purpose:** The `git push` command uploads local commits to a remote repository.

**Syntax:**

```bash
git push origin main
```

**Practical example:**

```bash
git add README.md
git commit -m "Document remote Git commands"
git push origin main
```

These commands stage the README changes, create a local commit, and attempt to upload them to the remote `main` branch.

**Use case:** Share completed work with teammates through GitHub.

**Common mistakes:**

- Pushing before committing changes.
- Pushing to the wrong branch.
- Trying to push when the remote contains commits your branch does not have.
- Pushing directly to a protected branch without permission.

**Tip:** In a team project, work on your own branch and push it before opening a pull request.

### 4.5 Git Rebase

**Purpose:** The `git rebase` command reapplies commits from one branch on top of another commit or branch. It can create a more linear project history.

**Syntax:**

```bash
git rebase main
```

**Practical example:**

```bash
git switch kenia-documentation
git fetch origin
git rebase origin/main
```

This switches to your working branch, downloads remote updates, and reapplies your branch's commits on top of `origin/main`.

**Use case:** Update your feature branch with the latest changes from the shared main branch.

**Handling a conflict:**

1. Open the conflicted file and resolve the conflict markers.
2. Stage the resolved file:

```bash
git add README.md
```

3. Continue the rebase:

```bash
git rebase --continue
```

To cancel the rebase and return to the previous state:

```bash
git rebase --abort
```

**Common mistakes:**

- Rebasing a branch that other people are using without coordinating.
- Forgetting to resolve all conflicts before continuing.
- Assuming that rebase creates a merge commit. Normally, it replays commits instead.

**Important:** Avoid rebasing shared commits that teammates depend on because rebase rewrites commit history.

### 4.6 Git Reset

**Purpose:** The `git reset` command moves the current branch pointer to another commit and, depending on the option, changes the staging area or working files.

**Commands:**

```bash
git reset --soft HEAD~1
git reset --mixed HEAD~1
git reset --hard HEAD~1
```

**Explanation:**

- `--soft`: Moves the branch back one commit but keeps changes staged.
- `--mixed`: Moves the branch back one commit and keeps changes in the working directory unstaged. This is the default mode.
- `--hard`: Moves the branch back one commit and discards changes in the index and tracked working files that differ from the target commit.

**Practical example:**

```bash
git reset --soft HEAD~1
```

This undoes the most recent local commit while keeping its changes staged so you can create another commit.

**Use case:** Correct a recent local commit before sharing it with teammates.

**Common mistakes:**

- Using `--hard` without understanding that it can permanently discard uncommitted changes.
- Resetting commits that have already been shared with others.
- Confusing `git reset` with `git revert`.

**Important:** Check `git status` and save important work before using reset. Avoid destructive commands unless you understand the consequences.

### 4.7 Git Revert

**Purpose:** The `git revert` command creates a new commit that reverses the changes introduced by an earlier commit. It preserves the existing commit history.

**Syntax:**

```bash
git revert COMMIT_ID
```

**Practical example:**

```bash
git log --oneline
git revert abc1234
```

Replace `abc1234` with the actual commit ID you want to reverse.

**Use case:** Undo an incorrect change that has already been pushed to a shared repository without removing the original commit from history.

**Common mistakes:**

- Using an incorrect commit ID.
- Forgetting that reverting creates a new commit rather than removing the old one.
- Failing to resolve conflicts that may occur during a revert.

**Tip:** Use `git log --oneline` to identify the correct commit before reverting it.

### 4.8 Difference Between Git Reset and Git Revert

| Feature | `git reset` | `git revert` |
|---|---|---|
| Main purpose | Moves the current branch to an earlier commit | Creates a commit that reverses an earlier change |
| History | Can rewrite local history | Preserves existing history |
| Best used for | Correcting local, unshared commits | Undoing changes in shared history |
| Creates a new commit | No | Yes |

**Example:**

Use `git reset --soft HEAD~1` to undo your latest local commit while keeping its changes staged.

Use `git revert COMMIT_ID` to reverse a change that has already been shared with teammates.

### 4.9 Practical Team Collaboration Workflow

The following example shows how a team member can update their branch, commit documentation changes, and push the branch to GitHub.

```bash
git status
git switch -c kenia-documentation
git fetch origin
git rebase origin/main
git add README.md
git commit -m "Add remote and advanced Git commands"
git push -u origin kenia-documentation
```

**Explanation:**

1. `git status` checks the current working tree.
2. `git switch -c` creates and switches to a new branch.
3. `git fetch origin` downloads remote updates.
4. `git rebase origin/main` updates the branch using the latest remote main branch.
5. `git add README.md` stages the documentation.
6. `git commit` saves the changes locally.
7. `git push -u` publishes the branch and sets its upstream tracking branch.

After pushing, open a pull request on GitHub so teammates can review the work before merging it.

**Note:** This example assumes `origin/main` exists and you have permission to push to the repository. If the team uses a different default branch or branch naming convention, adapt the commands accordingly.

## 5. Branching and Collaboration — Roxane

Branches let you work on a feature, a bug fix, or an experiment without touching the stable code. Each branch is an independent line of development, and you merge it back when the work is ready. This is the foundation of teamwork in Git.

### 5.1 git branch

`git branch` lists, creates, renames, and deletes branches. It does **not** move you onto a branch; use `git switch` for that.

**Syntax**

```bash
git branch
git branch -a
git branch <name>
git branch -m <old> <new>
git branch -d <name>
git branch -D <name>
```

**Explanation:**

- `git branch` lists local branches.
- `git branch -a` lists local and remote branches.
- `git branch <name>` creates a new branch at the current commit.
- `git branch -m <old> <new>` renames a branch.
- `git branch -d <name>` deletes a branch that has already been merged.
- `git branch -D <name>` force-deletes a branch, even if it is unmerged.

**Example:**

```bash
git branch feature/login
git branch
```

**Use case:** Create a branch for each task so `main` stays stable.

**Naming tip:** Use short, descriptive names such as `feature/login`, `fix/navbar-bug`, or `docs/git-guide`.

### 5.2 git switch

`git switch` moves you to another branch. It was introduced in Git 2.23 as a clearer alternative to `git checkout`.

**Syntax:**

```bash
git switch <branch>
git switch -c <new-branch>
git switch -
```

- `git switch <branch>` moves to an existing branch.
- `git switch -c <new-branch>` creates and switches to a new branch.
- `git switch -` returns to the previous branch.

**Example:**

```bash
git switch -c feature/login
git add .
git commit -m "feat: add login form"
git switch main
```

When you switch branches, the files in your working folder change to match that branch.

**Use case:** Move between feature work and `main` when needed.

**Older equivalent:** `git checkout <branch>` and `git checkout -b <new-branch>` perform similar operations.

### 5.3 git merge

`git merge` combines the history of one branch into the branch you are currently on.

**Syntax:**

```bash
git merge <branch>
git merge --no-ff <branch>
git merge --abort
```

**Step-by-step example:**

```bash
git switch main
git pull origin main
git merge feature/login
git branch -d feature/login
```

These commands switch to `main`, update it, merge `feature/login`, and delete the feature branch after it has been merged.

**Two kinds of merge:**

| Type | When it happens | Result |
|---|---|---|
| **Fast-forward** | The target branch has no new commits since the feature branch was created | Git moves the branch pointer forward without a merge commit |
| **Three-way merge** | Both branches have new commits | Git combines the histories, usually with a merge commit |

**Use case:** Merge a completed and reviewed feature into `main`.

### 5.4 Merge Conflicts and How to Resolve Them

A **merge conflict** happens when two branches change the same lines of a file, or one branch deletes a file that another edits, and Git cannot decide which changes to keep.

**Step 1: Identify the conflict.**

```bash
git merge feature/login
git status
```

Git lists conflicted files under “Unmerged paths.”

**Step 2: Understand the conflict markers.**

- Between `<<<<<<< HEAD` and `=======` is the current branch's version.
- Between `=======` and `>>>>>>> feature/login` is the incoming branch's version.

**Step 3: Edit the file.**

Keep the correct content or combine both versions. Remove all conflict-marker lines.

For example, the resolved file might contain:

```html
<h1>Welcome to the Student Portal</h1>
```

**Step 4: Finish the merge.**

```bash
git add index.html
git commit
```

**Other useful commands:**

```bash
git merge --abort
git checkout --ours <file>
git checkout --theirs <file>
git diff --name-only --diff-filter=U
```

- `git merge --abort` cancels an in-progress merge.
- `git checkout --ours <file>` keeps the current branch's version of a conflicted file.
- `git checkout --theirs <file>` keeps the incoming branch's version.
- `git diff --name-only --diff-filter=U` lists files that remain conflicted.

**How to avoid conflicts:**

- Pull from `main` regularly.
- Keep branches small and short-lived.
- Communicate with teammates before editing the same file.

### 5.5 git stash

`git stash` temporarily saves uncommitted changes so you can switch tasks with a clean working directory and restore the changes later.

**Syntax:**

```bash
git stash
git stash push -m "message"
git stash -u
git stash list
git stash pop
git stash apply stash@{1}
git stash drop stash@{0}
git stash clear
```

**Explanation:**

- `git stash` saves changes to tracked files.
- `git stash push -m "message"` saves changes with a descriptive message.
- `git stash -u` also includes untracked files.
- `git stash list` lists saved stashes.
- `git stash pop` restores the latest stash and removes it from the stash list if successful.
- `git stash apply stash@{1}` restores a specific stash while keeping it in the list.
- `git stash drop stash@{0}` deletes a specific stash.
- `git stash clear` deletes all saved stashes.

**Example:**

```bash
git stash push -m "half-done login form"
git switch main
git switch -c fix/urgent-bug
```

After fixing and committing the urgent bug, return to your feature branch and restore the saved work:

```bash
git switch feature/login
git stash pop
```

**Use case:** Temporarily set aside unfinished work to handle another task.

### 5.6 Real-World Teamwork Examples

**Example 1: Feature-branch workflow**

```bash
git switch main
git pull origin main
git switch -c feature/contact-page
git add .
git commit -m "feat: add contact page"
git push -u origin feature/contact-page
```

Then open a pull request on GitHub, ask a teammate to review it, and merge it into `main` once approved.

After merging, clean up:

```bash
git switch main
git pull origin main
git branch -d feature/contact-page
```

**Example 2: Two teammates edit the same file**

1. Two teammates start from `main` and create separate branches.
2. Both edit the same line in `README.md`.
3. The first teammate's pull request is merged.
4. The second teammate updates their branch and resolves any conflicts.
5. They stage and commit the resolved file, then push the branch.
6. Their pull request can be reviewed and merged.

**Example 3: Interrupted by an urgent bug**

Use `git stash` to save unfinished work, fix the bug on a separate branch, and return to the original task with `git stash pop`.

**Suggested team rules:**

- Avoid committing directly to `main`; use branches and pull requests.
- Create one branch per feature or fix.
- Pull regularly and coordinate with teammates before integrating changes.
- Write meaningful commit messages, such as `fix: correct footer link`.

### 5.7 Quick Reference

| Task | Command |
|---|---|
| List branches | `git branch` |
| Create a branch | `git branch <name>` |
| Create and switch | `git switch -c <name>` |
| Switch branches | `git switch <name>` |
| Merge a branch | `git merge <name>` |
| Abort a merge | `git merge --abort` |
| Delete a merged branch | `git branch -d <name>` |
| Save changes in a stash | `git stash push -m "message"` |
| Restore the latest stash | `git stash pop` |

## Merge Conflict Resolution
This section demonstrates resolving conflicting changes during collaboration.
