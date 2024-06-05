# 🚀 Introduction to Git and Git Architecture

## 📚 Overview

Welcome to Week 3 of my internship! This week, we will dive into Git, a powerful version control system. Let's explore the essentials of Git, its architecture, and how it facilitates efficient project management.

## 🔄 Version Control System (VCS) and Its Types

A Version Control System (VCS) allows multiple developers to collaborate on a project, track changes, and maintain a history of work. The two main types of VCS are:

- **Centralized VCS (CVCS)**: A single central repository that all users interact with (e.g., Subversion, CVS).
- **Distributed VCS (DVCS)**: Each user has a local copy of the repository (e.g., Git, Mercurial).

## 🧠 Git Concepts and Terminologies

- **Clone**: 📥 Copy a remote repository to your local machine.
- **Branch**: 🌿 Create a parallel version of the repository to work on changes independently.
- **Checkout**: 🚀 Switch between different branches or commits.
- **Commit**: 💾 Save changes to the local repository with a message.
- **Push**: 🚀 Upload local changes to a remote repository.
- **Pull**: 📥 Fetch and merge changes from a remote repository to your local machine.
- **Log**: 📝 View the history of commits.
- **Add**: ➕ Stage changes for the next commit.
- **Reset**: 🔄 Undo changes in the local repository.
- **Revert**: ⏪ Create a new commit that undoes changes from a previous commit.

## 🌲 Git Branching and Merging Strategies

- **Branching**: Create branches for new features, bug fixes, or experiments without affecting the main codebase.
- **Merging**: Integrate changes from different branches. Common strategies include:
  - **Fast-Forward Merge**: When the target branch has not diverged.
  - **Three-Way Merge**: When there are multiple commits from both branches.
- **Merge Conflicts**: Occur when changes in different branches conflict. Resolve conflicts manually by editing the affected files.

## 🌐 Git Protocols

- **HTTPS**: Secure and easy to set up.
- **SSH**: Provides secure communication and is ideal for private repositories.
- **Git Protocol**: Fast but less secure, typically used within trusted networks.

## 📂 Git Basic Commands and Managing Repositories

- `git init` ➡️ Initialize a new Git repository.
- `git clone <repo-url>` ➡️ Clone an existing repository.
- `git add <file>` ➡️ Stage file changes.
- `git commit -m "message"` ➡️ Commit staged changes.
- `git push` ➡️ Push changes to the remote repository.
- `git pull` ➡️ Pull changes from the remote repository.
- `git status` ➡️ Check the status of the working directory.
- `git log` ➡️ View commit history.

## 🚦 Git Workflow Strategies

- **Feature Branch Workflow**: Develop new features in separate branches.
- **Gitflow Workflow**: Structured branching model with feature, release, and hotfix branches.
- **Forking Workflow**: Use forks for independent development and collaboration.

## 🪝 Git Hooks

Git hooks are scripts that run automatically at certain points in the Git workflow. They are useful for enforcing policies and automating tasks.

- **Pre-commit**: Run before a commit is made.
- **Post-commit**: Run after a commit is made.
- **Pre-push**: Run before pushing changes to a remote repository.

