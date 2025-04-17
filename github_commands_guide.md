# GitHub Commands Guide

## Basic Git Commands

| Command | Description |
|---------|-------------|
| `git init .` | Create a new Git repository in the current directory |
| `git add <filename>` | Start tracking a file |
| `git commit -a -m "message"` | Commit all changes with a descriptive message |
| `git status` | Check the current state of your repository |
| `git log` | View commit history |

## Remote Repository Management

| Command | Description |
|---------|-------------|
| `git remote add origin <url>` | Link your local repository to a remote repository |
| `git branch -M main` | Rename the current branch to 'main' |
| `git push -u origin main` | Push your changes to the remote repository |

## File Management

| Command | Description |
|---------|-------------|
| `git rm --cached <file>` | Remove a file from Git tracking (keeps the file locally) |
| `git reset --hard HEAD~1` | Undo the last commit and all changes |
| `git revert <commit-id>` | Create a new commit that undoes changes from a specific commit |
| `git commit --amend -m "message"` | Modify the last commit message |

## Virtual Environment

| Command | Description |
|---------|-------------|
| `.\venv\Scripts\Activate` | Activate the virtual environment (Windows PowerShell) |

## Best Practices

1. Always write clear, descriptive commit messages
2. Commit related changes together
3. Push your changes regularly to keep your remote repository up to date
4. Use branches for new features or bug fixes
5. Keep sensitive information out of your repository (use .gitignore)

## Common Workflow

1. Initialize repository: `git init .`
2. Add files: `git add <filename>`
3. Make changes and commit: `git commit -a -m "message"`
4. Link to remote: `git remote add origin <url>`
5. Push changes: `git push -u origin main`

## Troubleshooting

- If you accidentally commit sensitive information:
  - Remove the file from tracking: `git rm --cached <file>`
  - Add the file to .gitignore
  - Commit the changes
  - Push to remote

- To undo the last commit:
  - `git reset --hard HEAD~1` (if you want to completely remove the commit)
  - `git revert <commit-id>` (if you want to keep a record of the undo) 