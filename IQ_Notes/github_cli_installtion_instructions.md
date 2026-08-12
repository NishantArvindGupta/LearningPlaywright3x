# GitHub CLI Installation and Setup Instructions

This document explains how to install, configure, and use GitHub CLI (`gh`) on Ubuntu, along with a simple workflow for cloning and pushing a repository.

---

## 1. Install GitHub CLI on Ubuntu

Open the terminal and run:

```bash
sudo apt update
sudo apt install gh
gh --version
```

If `gh` is not available from the default Ubuntu repositories, you can install it using the official package source.

### Optional official install method

```bash
type -p curl >/dev/null || sudo apt install curl
curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | sudo dd of=/usr/share/keyrings/githubcli-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null
sudo apt update
sudo apt install gh
```

---

## 2. Configure GitHub CLI

Run the login command:

```bash
gh auth login
```

When prompted, choose:

- `GitHub.com`
- `HTTPS`
- `Login with a web browser`

Then open the URL shown in the terminal, paste the one-time code, and authorize the app in your browser.

To verify the authentication status, run:

```bash
gh auth status
```

If you prefer using a token directly, you can also do:

```bash
gh auth login --with-token < token.txt
```

---

## 3. Basic GitHub CLI Commands

Some common commands are:

```bash
gh repo view
gh issue list
gh pr list
gh pr create
gh repo clone OWNER/REPO
gh release list
```

You can also set a default editor for GitHub CLI if needed:

```bash
gh config set editor "code --wait"
```

And configure your Git identity in Git:

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

---

## 4. Simple workflow: clone and push a repository with GitHub CLI

### Step 1: Clone a repository

```bash
gh repo clone OWNER/repo-name
cd repo-name
```

Example:

```bash
gh repo clone microsoft/vscode
cd vscode
```

### Step 2: Create a branch

```bash
git checkout -b my-feature
```

### Step 3: Make changes

```bash
echo "hello" >> notes.txt
git add notes.txt
git commit -m "Add notes"
```

### Step 4: Push to GitHub

```bash
git push -u origin my-feature
```

### Step 5: Create a pull request

```bash
gh pr create --fill
```

This creates a pull request from the current branch.

---

## 5. Create a new GitHub repository from a local project

If you want to create a new repo on GitHub from a local folder, use:

```bash
cd /path/to/your/project
git init
git add .
git commit -m "Initial commit"
gh repo create my-repo --public --source=. --remote=origin --push
```

This creates the repository on GitHub and pushes the current folder to it.

---

## 6. Useful extra commands

```bash
gh repo view
gh issue list
gh pr list
gh auth logout
```

---

## Summary

To configure GitHub CLI on Ubuntu:

```bash
sudo apt update
sudo apt install gh
gh auth login
gh auth status
```

Then use `gh repo clone`, `git push`, and `gh pr create` to work with GitHub efficiently from the terminal.

---

## Final note

GitHub CLI makes GitHub operations easier directly from the command line, including repo cloning, pull request creation, issue management, and authentication setup.
