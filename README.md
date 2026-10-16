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
