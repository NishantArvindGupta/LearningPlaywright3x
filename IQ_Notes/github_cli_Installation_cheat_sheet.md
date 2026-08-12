# GitHub CLI Cheat Sheet

## Install

```bash
sudo apt update
sudo apt install gh
gh --version
```

## Login

```bash
gh auth login
```

Choose:
- `GitHub.com`
- `HTTPS`
- `Login with a web browser`

Verify:

```bash
gh auth status
```

## Clone a repo

```bash
gh repo clone OWNER/repo-name
cd repo-name
```

## Create branch

```bash
git checkout -b my-feature
```

## Commit and push

```bash
git add .
git commit -m "Your message"
git push -u origin my-feature
```

## Create pull request

```bash
gh pr create --fill
```

## Create repo from local folder

```bash
cd /path/to/project
git init
git add .
git commit -m "Initial commit"
gh repo create my-repo --public --source=. --remote=origin --push
```

## Useful commands

```bash
gh repo view
gh issue list
gh pr list
gh release list
gh config set editor "code --wait"
gh auth logout
```

## Quick flow

```bash
sudo apt install gh
gh auth login
gh repo clone OWNER/repo-name
cd repo-name
git checkout -b feature-branch
git push -u origin feature-branch
gh pr create --fill
```

## Reminder

GitHub CLI helps you do GitHub tasks from the terminal without opening the browser for every action.
