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

**Command:**

```bash
git init
```

**Explanation:** Initializes a new Git repository in the current directory.

**Use case:** Start tracking changes in a new project.

### 2.3 Clone a Repository

**Command:**

```bash
git clone https://github.com/USERNAME/REPOSITORY.git
```

**Explanation:** Downloads a copy of a remote repository to your computer.

**Use case:** Get a copy of an existing team project to work on locally.

### 2.4 Check Repository Status

**Command:**

```bash
git status
```

**Explanation:** Displays changed, staged, and untracked files.

**Use case:** Check which files need to be staged or committed.

### 2.5 Stage Changes

**Commands:**

```bash
git add README.md
git add .
```

**Explanation:** Adds changes to the staging area before committing.

**Use case:** Select the changes you want to include in the next commit.

### 2.6 Commit Changes

**Command:**

```bash
git commit -m "Add essential Git commands"
```

**Explanation:** Records staged changes in the local repository.

**Use case:** Save a meaningful unit of work with a descriptive commit message.

### 2.7 View Commit History

**Commands:**

```bash
git log
git log --oneline
```

**Explanation:** Displays the history of commits in the repository.

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

These commands stage the README changes, create a local commit, and attempt to upload it to the remote `main` branch.

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