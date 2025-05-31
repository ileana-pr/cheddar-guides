# 🔄 GitHub Commands Guide

<div align="center">
  <i>Essential Git and GitHub commands for effective version control</i>
</div>

---

## 📋 Table of Contents
- [Basic Git Commands](#basic-git-commands)
- [Repository Cloning](#repository-cloning)
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

## 📥 Repository Cloning

### Finding Repository URLs on GitHub

Before you can clone a repository, you need to get its URL from GitHub:

1. **Navigate to the repository** on GitHub.com
2. **Click the green "Code" button** (located above the file list)
3. **Choose your preferred method:**

| Method | When to Use | Location in Code Dropdown |
|--------|-------------|---------------------------|
| **HTTPS** | Default option, works everywhere | Selected by default, starts with `https://` |
| **SSH** | When you have SSH keys set up ([see our SSH guide](github_ssh_setup.md)) | Click "SSH" tab, starts with `git@` |
| **GitHub CLI** | When using GitHub CLI tool | Click "GitHub CLI" tab, starts with `gh repo clone` |

4. **Copy the URL** by clicking the copy button (📋) next to the URL

### Visual Guide to Finding URLs

```
GitHub Repository Page
├── Repository name and description
├── 📊 Code | Issues | Pull requests | Actions | Projects | Wiki | Security | Insights
├── 📁 Branch selector (main ▼) | 🔄 commits | 📋 Code ▼  <-- Click this green button
│   └── Code dropdown menu:
│       ├── 🔗 HTTPS: https://github.com/username/repo.git
│       ├── 🔑 SSH: git@github.com:username/repo.git  
│       └── 💻 GitHub CLI: gh repo clone username/repo
└── 📁 File and folder listing
```

### Basic Cloning Commands

| Command | Description |
|---------|-------------|
| `git clone <repository-url>` | Clone a repository to your local machine |
| `git clone <repository-url> <directory-name>` | Clone a repository into a specific directory |
| `git clone --depth 1 <repository-url>` | Shallow clone (only latest commit, faster for large repos) |
| `git clone -b <branch-name> <repository-url>` | Clone a specific branch |

### Clone URL Formats

| Protocol | URL Format | Example |
|----------|------------|---------|
| **HTTPS** | `https://github.com/username/repo.git` | `git clone https://github.com/octocat/Hello-World.git` |
| **SSH** | `git@github.com:username/repo.git` | `git clone git@github.com:octocat/Hello-World.git` |
| **GitHub CLI** | `gh repo clone username/repo` | `gh repo clone octocat/Hello-World` |

### Post-Clone Setup

After cloning a repository, you typically want to:

```bash
# navigate into the cloned directory
cd repository-name

# check the remote configuration
git remote -v

# check current branch
git branch

# check status
git status
```

### Common Cloning Scenarios

| Scenario | Command | Use Case |
|----------|---------|----------|
| **Fork and Clone** | `git clone git@github.com:yourusername/forked-repo.git` | Working on a forked repository |
| **Large Repository** | `git clone --depth 1 <url>` | Quick download without full history |
| **Specific Branch** | `git clone -b develop <url>` | Start working on a specific branch |
| **Custom Directory** | `git clone <url> my-project` | Clone into a custom-named folder |

### Setting Up Upstream (for Forks)

When working with forks, set up the original repository as upstream:

```bash
# clone your fork
git clone git@github.com:yourusername/forked-repo.git
cd forked-repo

# add the original repository as upstream
git remote add upstream git@github.com:originalowner/original-repo.git

# verify remotes
git remote -v
# should show:
# origin    git@github.com:yourusername/forked-repo.git (fetch)
# origin    git@github.com:yourusername/forked-repo.git (push)
# upstream  git@github.com:originalowner/original-repo.git (fetch)
# upstream  git@github.com:originalowner/original-repo.git (push)
```

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

### Starting from Scratch
1. Initialize repository: `git init .`
2. Add files: `git add <filename>`
3. Make changes and commit: `git commit -a -m "message"`
4. Link to remote: `git remote add origin <url>`
5. Push changes: `git push -u origin main`

### Starting by Cloning
1. Clone repository: `git clone <repository-url>`
2. Navigate to directory: `cd repository-name`
3. Make changes to files
4. Stage changes: `git add <filename>` or `git add .`
5. Commit changes: `git commit -m "descriptive message"`
6. Push changes: `git push`

### Working with Forks
1. Clone your fork: `git clone git@github.com:yourusername/forked-repo.git`
2. Set up upstream: `git remote add upstream <original-repo-url>`
3. Create feature branch: `git checkout -b feature-name`
4. Make changes and commit: `git commit -m "message"`
5. Push to your fork: `git push origin feature-name`
6. Create pull request on GitHub

---

## 🛠️ Troubleshooting

### Repository Cloning Issues

#### Can't Find the "Code" Button?
- **Private Repository**: Make sure you're logged into GitHub and have access to the repository
- **Organization Repository**: Check if you have the necessary permissions
- **Archived Repository**: Archived repos can still be cloned but may show differently

#### Clone Permission Denied?
```bash
# Error: Permission denied (publickey)
# Solution: Use HTTPS instead of SSH, or set up SSH keys
git clone https://github.com/username/repo.git  # Use HTTPS
# OR set up SSH keys following our SSH guide
```

#### Repository Not Found?
- **Check the URL**: Make sure you copied the complete URL
- **Private Repository**: Ensure you have access and are logged in
- **Typo in Username/Repo**: Double-check the repository name and owner

#### HTTPS vs SSH Decision Guide
| Use HTTPS when: | Use SSH when: |
|----------------|---------------|
| ✅ First time using Git/GitHub | ✅ You have SSH keys set up |
| ✅ Working on public repositories | ✅ You push code frequently |
| ✅ Behind corporate firewall | ✅ You want password-free authentication |
| ✅ Quick one-time clone | ✅ Working with private repositories regularly |

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