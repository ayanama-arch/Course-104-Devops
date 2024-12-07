# Getting Started

## Version Control Overview

**Version control** is a system that tracks changes to files over time, allowing you to revert to previous versions, compare changes, and collaborate efficiently. It’s commonly used in software development to manage source code but can be applied to any file type.

### Types of Version Control Systems (VCS):

1. **Local Version Control Systems (VCS)**:

   - Involves manually copying files to different directories to keep track of versions (e.g., time-stamped folders).
   - **RCS** was a popular local VCS, which kept a history of changes using patch sets (differences between file versions).
   - **Problem**: It’s easy to overwrite files or make mistakes while managing directories manually.

2. **Centralized Version Control Systems (CVCS)**:

   - A **central server** holds all files, and multiple clients access and update files from this server (e.g., CVS, Subversion).
   - **Advantages**:
     - Everyone knows what others are working on.
     - Fine-grained control over user permissions.
   - **Problems**:
     - **Single point of failure**: If the central server goes down, no one can access or update files.
     - If the server is lost (e.g., due to corruption), the entire project history is lost.

3. **Distributed Version Control Systems (DVCS)**:
   - Clients don’t just pull the latest version of files; they **mirror the entire repository** with its full history (e.g., **Git**).
   - **Advantages**:
     - **Redundancy**: Every client has a full backup of the project, so if the server goes down, anyone with a copy can restore it.
     - More flexible collaboration with multiple remote repositories and workflows.
   - **Examples**: Git, Mercurial, Darcs.

## What is Git?

Git is a **version control system (VCS)** that helps developers track and manage changes in their code over time. It’s different from other version control systems (like Subversion) in how it stores and handles data.

### Key Concepts:

1. **Snapshots, Not Changes:**

   - Other version control systems (VCS) track changes to files over time.
   - **Git**, however, takes **snapshots** of the entire project at each commit. It saves the state of all files at that moment.
   - If a file hasn’t changed, Git doesn’t store it again, just a reference to the previous snapshot.

2. **Local Operations:**

   - Most Git operations are local. This means you can work offline, make changes, and commit without needing a connection to a remote server.
   - Operations like viewing project history or comparing changes are fast because Git stores everything locally.

3. **Git Has Integrity:**

   - Git ensures data integrity by using **SHA-1 hashes** (unique identifiers) for every file and commit.
   - If any file is changed or corrupted, Git will detect it because the hash would no longer match.

4. **Git Generally Only Adds Data:**

   - When you perform actions in Git (like committing changes), it generally **adds** data to the database, making it difficult to lose data once it’s committed.
   - You can experiment with your code without worrying about losing important data.

5. **The Three States of Files:**
   - **Modified**: The file has been changed, but not saved in Git yet.
   - **Staged**: The file has been marked to be included in the next commit.
   - **Committed**: The file is saved in Git’s database.

### The Three Main Areas in Git:

1. **Working Tree**: Where you modify files.
2. **Staging Area**: A temporary place to store changes before committing them.
3. **Git Directory**: The database where Git stores all the project’s history and metadata.

### Basic Git Workflow:

1. **Modify files** in the working tree.
2. **Stage** the changes you want to commit.
3. **Commit** those staged changes to Git’s database.

This way, Git helps you easily track, manage, and roll back changes to your code as needed.

## Basic Setup

### Git Configuration Overview

When you first set up Git, you'll need to configure some important settings. You only need to do this once per machine. These settings are stored in different places and Git reads them in a specific order:

1. **System-wide settings** (`/etc/gitconfig`): Applies to all users on the system. Requires admin privileges to modify.
2. **User-specific settings** (`~/.gitconfig` or `~/.config/git/config`): Applies only to the current user. This is where you'll set things like your name and email.
3. **Repository-specific settings** (`.git/config` inside the repo): Applies only to a specific repository.

### Key Configuration Steps:

1. **Set Your Identity**: Git needs your name and email to track who makes the changes in the repository.

   ```bash
   git config --global user.name "John Doe"
   git config --global user.email "johndoe@example.com"
   ```

2. **Set Your Editor**: Git uses a text editor when it needs you to enter commit messages. You can choose your preferred editor.
   Example for **Emacs**:

   ```bash
   git config --global core.editor emacs
   ```

   For **Notepad++** (Windows):

   ```bash
   git config --global core.editor "'C:/Program Files/Notepad++/notepad++.exe' -multiInst -notabbar -nosession -noPlugin"
   ```

3. **Set the Default Branch Name**: Git uses "master" as the default branch name. You can change this to "main" if you prefer.

   ```bash
   git config --global init.defaultBranch main
   ```

4. **Check Your Configuration**: To see your settings, use:
   ```bash
   git config --list
   ```
   To check a specific setting, like your username:
   ```bash
   git config user.name
   ```

### Configuration Hierarchy

- **Repository-specific** settings override **user-specific** settings.
- **User-specific** settings override **system-wide** settings.

You can also use `git config --show-origin` to see where a setting came from if you're unsure.
