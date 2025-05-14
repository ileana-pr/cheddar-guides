# 🔄 GitHub Commands Guide

<div align="center">
  <i>Essential Git and GitHub commands for effective version control</i>
</div>

---

## 📋 Table of Contents
- [Basic Git Commands](#basic-git-commands)
- [Remote Repository Management](#remote-repository-management)
- [File Management](#file-management)
- [Virtual Environment](#virtual-environment)
- [Best Practices](#best-practices)
- [Common Workflow](#common-workflow)
- [Troubleshooting](#troubleshooting)

---

## 🏁 Basic Git Commands

| Command | Description |
|---------|-------------|
| `git init .` | Create a new Git repository in the current directory |
| `git add <filename>` | Start tracking a file |
| `git commit -a -m "message"` | Commit all changes with a descriptive message |
| `git status` | Check the current state of your repository |
| `git log` | View commit history |

---

## 🌐 Remote Repository Management

| Command | Description |
|---------|-------------|
| `git remote add origin <url>` | Link your local repository to a remote repository |
| `git branch -M main` | Rename the current branch to 'main' |
| `git push -u origin main` | Push your changes to the remote repository |

---

## 🔄 Managing Origin and Upstream

| Command | Description |
|---------|-------------|
| `git remote -v` | View all remote repositories |
| `git remote remove origin` | Remove the current origin remote |
| `git remote add upstream <original-repo-url>` | Add the original repository as upstream |
| `git remote set-url origin <new-repo-url>` | Change the URL of the origin remote |
| `git fetch upstream` | Fetch changes from the upstream repository |
| `git merge upstream/main` | Merge changes from upstream's main branch |
| `git push origin main --force` | Force push to origin (use with caution!) |

---

## 📁 File Management

| Command | Description |
|---------|-------------|
| `git rm --cached <file>` | Remove a file from Git tracking (keeps the file locally) |
| `git reset --hard HEAD~1` | **DANGER!** Discard all uncommitted changes and unstaged files, and reset the current branch to the commit before HEAD. *Use with extreme caution as this can lead to data loss.* |
| `git reset --hard <commit-id>` | **DANGER!** Discard all uncommitted changes and unstaged files, and reset the current branch to the specified `<commit-id>`. *Irreversibly loses all subsequent commits and changes.* |
| `git reset --hard origin/main` | **DANGER!** Discard all local changes and commits on the current branch, and reset it to match the state of `origin/main`. *Use to discard local work and sync with the remote. Ensure `origin/main` is fetched and up-to-date.* |
| `git revert <commit-id>` | Create a new commit that undoes changes from a specific commit (safer than `reset --hard` for shared history) |
| `git commit --amend -m "message"` | Modify the last commit message |

---

## 🔧 Virtual Environment

| Command | Description |
|---------|-------------|
| `.\venv\Scripts\Activate` | Activate the virtual environment (Windows PowerShell) |

---

## 💡 Best Practices

1. Always write clear, descriptive commit messages
2. Commit related changes together
3. Push your changes regularly to keep your remote repository up to date
4. Use branches for new features or bug fixes
5. Keep sensitive information out of your repository (use .gitignore)

---

## 🔄 Common Workflow

1. Initialize repository: `git init .`
2. Add files: `git add <filename>`
3. Make changes and commit: `git commit -a -m "message"`
4. Link to remote: `git remote add origin <url>`
5. Push changes: `git push -u origin main`

---

## 🛠️ Troubleshooting

### Sensitive Information Issues
- If you accidentally commit sensitive information:
  ```bash
  # Remove the file from tracking
  git rm --cached <file>
  
  # Add the file to .gitignore
  echo "<file>" >> .gitignore
  
  # Commit the changes
  git commit -m "Remove sensitive file from tracking"
  
  # Push to remote
  git push
  ```

### Undoing Commits
- To completely remove the last commit:
  ```bash
  git reset --hard HEAD~1
  ```
- To keep a record of the undo:
  ```bash
  git revert <commit-id>
  ```

---

<div align="center">
  <p><strong>Happy version controlling!</strong></p>
</div> 