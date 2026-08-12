# GitHub CLI Study Notes

## Overview

GitHub CLI (`gh`) is a command-line tool that lets you interact with GitHub directly from the terminal. It helps with authentication, repository management, pull requests, issues, and general GitHub workflow tasks without needing to open the browser for every action.

---

## Why use GitHub CLI?

GitHub CLI is useful because it:

- Simplifies authentication with GitHub
- Makes cloning repositories easier
- Helps create and manage pull requests from the terminal
- Allows quick access to repository and issue information
- Improves developer productivity for terminal-based workflows

---

## Installing GitHub CLI on Ubuntu

The simplest installation on Ubuntu is:

```bash
sudo apt update
sudo apt install gh
gh --version
```

This checks whether the GitHub CLI is installed correctly.

If the package is not available in default repositories, use the official GitHub CLI apt source:

```bash
type -p curl >/dev/null || sudo apt install curl
curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | sudo dd of=/usr/share/keyrings/githubcli-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null
sudo apt update
sudo apt install gh
```

---

## Configuring GitHub CLI

To log in to your GitHub account:

```bash
gh auth login
```

Follow the prompt flow:

1. Select `GitHub.com`
2. Choose `HTTPS`
3. Choose `Login with a web browser`
4. Copy the code shown in the terminal
5. Open the URL in your browser and authorize GitHub CLI

To verify the login:

```bash
gh auth status
```

This confirms that GitHub CLI is authenticated and ready to use.

---

## Common GitHub CLI Commands

### Repository commands

```bash
gh repo view
gh repo clone OWNER/repo-name
```

### Issue and PR commands

```bash
gh issue list
gh pr list
gh pr create --fill
```

### Release commands

```bash
gh release list
```

### Configuration

```bash
gh config set editor "code --wait"
```

This sets VS Code as the default editor for commands that open editor-based prompts.

---

## Simple Workflow: Clone and Push a Repository

### 1. Clone a repository

```bash
gh repo clone OWNER/repo-name
cd repo-name
```

Example:

```bash
gh repo clone microsoft/vscode
cd vscode
```

### 2. Create a branch

```bash
git checkout -b my-feature
```

### 3. Make changes

```bash
echo "hello" >> notes.txt
git add notes.txt
git commit -m "Add notes"
```

### 4. Push the branch

```bash
git push -u origin my-feature
```

### 5. Create a pull request

```bash
gh pr create --fill
```

This will create a pull request for your branch based on the current branch context.

---

## Creating a New GitHub Repository from a Local Folder

If you already have a project locally and want to create a GitHub repository from it:

```bash
cd /path/to/your/project
git init
git add .
git commit -m "Initial commit"
gh repo create my-repo --public --source=. --remote=origin --push
```

This creates the remote repository and pushes the local files to it automatically.

---

## Example Full Flow

```bash
sudo apt update
sudo apt install gh
gh auth login
gh auth status
gh repo clone OWNER/repo-name
cd repo-name
git checkout -b feature-branch
echo "hello" >> demo.txt
git add demo.txt
git commit -m "Add demo file"
git push -u origin feature-branch
gh pr create --fill
```

---

## Key Takeaways

- `gh` is used to work with GitHub from the terminal.
- It requires authentication with `gh auth login`.
- It is especially useful for cloning repos, creating pull requests, and inspecting GitHub issues.
- It fits well into a developer workflow that prefers the terminal over the browser.

---

## Quick Summary

```bash
sudo apt install gh
gh auth login
gh auth status
gh repo clone OWNER/REPO
cd REPO
git checkout -b my-feature
git push -u origin my-feature
gh pr create --fill
```

This covers the essential GitHub CLI workflow for a beginner.
