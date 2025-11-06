# Git Commands Cheat Sheet

A comprehensive reference guide for commonly used Git commands.

## Table of Contents
- [Configuration](#configuration)
- [Creating & Cloning Repositories](#creating--cloning-repositories)
- [Basic Commands](#basic-commands)
- [Branching & Merging](#branching--merging)
- [Remote Repositories](#remote-repositories)
- [Inspecting & Comparing](#inspecting--comparing)
- [Undoing Changes](#undoing-changes)
- [Stashing](#stashing)
- [Tagging](#tagging)
- [Advanced Commands](#advanced-commands)

---

## Configuration

Configure user information for all local repositories.

```bash
# Set a name that is identifiable for credit when reviewing version history
git config --global user.name "[firstname lastname]"

# Set an email address that will be associated with each history marker
git config --global user.email "[valid-email]"

# Set automatic command line coloring for Git for easy reviewing
git config --global color.ui auto

# List all configuration settings
git config --list
```

---

## Creating & Cloning Repositories

Initialize or clone a repository.

```bash
# Initialize a new local repository
git init [project-name]

# Clone an existing repository
git clone [url]

# Clone a repository to a specific directory
git clone [url] [directory-name]
```

---

## Basic Commands

Essential day-to-day commands.

```bash
# Check the status of your repository
git status

# Add a file to staging area
git add [file]

# Add all changed files to staging area
git add .

# Commit your staged content as a new commit snapshot
git commit -m "[descriptive message]"

# Add and commit in one command
git commit -am "[descriptive message]"

# Show modified files in working directory
git diff

# Show staged changes
git diff --staged

# Remove files from the working directory and staging area
git rm [file]

# Move or rename a file
git mv [existing-path] [new-path]
```

---

## Branching & Merging

Manage branches and merge changes.

```bash
# List all branches in your repository
git branch

# Create a new branch
git branch [branch-name]

# Switch to a specific branch
git checkout [branch-name]

# Create and switch to a new branch
git checkout -b [branch-name]

# Switch to a branch (modern syntax)
git switch [branch-name]

# Create and switch to a new branch (modern syntax)
git switch -c [branch-name]

# Merge a branch into your current branch
git merge [branch-name]

# Delete a branch
git branch -d [branch-name]

# Force delete a branch
git branch -D [branch-name]

# List all remote branches
git branch -r

# List all local and remote branches
git branch -a
```

---

## Remote Repositories

Synchronize your local repository with remote repositories.

```bash
# List all remote connections
git remote -v

# Add a new remote repository
git remote add [alias] [url]

# Remove a remote connection
git remote remove [alias]

# Rename a remote connection
git remote rename [old-name] [new-name]

# Fetch changes from remote repository
git fetch [alias]

# Fetch and merge changes from remote branch
git pull [alias] [branch]

# Upload local branch commits to remote repository
git push [alias] [branch]

# Push all tags to remote
git push [alias] --tags

# Delete a remote branch
git push [alias] --delete [branch-name]
```

---

## Inspecting & Comparing

View project history and changes.

```bash
# Show commit history
git log

# Show commit history with diffs
git log -p

# Show commit history in one line per commit
git log --oneline

# Show commit history with graph
git log --graph --oneline --all

# Show commit history for a specific file
git log [file]

# Show changes in a specific commit
git show [commit-hash]

# Show who changed each line in a file
git blame [file]

# Show difference between two branches
git diff [branch1]..[branch2]

# Show files changed in a commit
git show --name-only [commit-hash]
```

---

## Undoing Changes

Revert or reset changes in your repository.

```bash
# Discard changes in working directory
git checkout -- [file]

# Restore file from a specific commit
git checkout [commit-hash] -- [file]

# Unstage a file while retaining changes
git reset [file]

# Reset staging area to match most recent commit
git reset

# Reset staging area and working directory to match commit
git reset --hard [commit-hash]

# Create a new commit that undoes all changes in a commit
git revert [commit-hash]

# Amend the last commit
git commit --amend

# Amend the last commit without changing message
git commit --amend --no-edit
```

---

## Stashing

Temporarily store modified, tracked files.

```bash
# Save modified and staged changes
git stash

# Save with a custom message
git stash save "[message]"

# List all stashes
git stash list

# Apply the most recent stash
git stash apply

# Apply a specific stash
git stash apply stash@{[n]}

# Apply and remove the most recent stash
git stash pop

# Drop a specific stash
git stash drop stash@{[n]}

# Clear all stashes
git stash clear

# Show the changes in the most recent stash
git stash show -p
```

---

## Tagging

Create and manage tags.

```bash
# List all tags
git tag

# Create a lightweight tag
git tag [tag-name]

# Create an annotated tag
git tag -a [tag-name] -m "[message]"

# Tag a specific commit
git tag [tag-name] [commit-hash]

# Show tag information
git show [tag-name]

# Delete a tag
git tag -d [tag-name]

# Push a tag to remote
git push [alias] [tag-name]

# Delete a remote tag
git push [alias] --delete [tag-name]
```

---

## Advanced Commands

More advanced Git operations.

```bash
# Rebase current branch onto another branch
git rebase [branch]

# Interactive rebase for the last n commits
git rebase -i HEAD~[n]

# Cherry-pick a commit from another branch
git cherry-pick [commit-hash]

# Show reference log
git reflog

# Clean untracked files from working directory
git clean -fd

# Clean ignored files as well
git clean -fdx

# Create a patch file
git format-patch [branch]

# Apply a patch file
git apply [patch-file]

# Find commits that introduced a bug using binary search
git bisect start
git bisect bad [commit-hash]
git bisect good [commit-hash]

# Show which branch contains a specific commit
git branch --contains [commit-hash]
```

---

## Tips & Best Practices

- Commit early and often
- Write meaningful commit messages
- Always pull before you push
- Use branches for new features
- Review changes before committing with `git diff`
- Keep commits focused on a single change
- Don't commit generated or temporary files
- Use `.gitignore` to exclude files from version control

---

## Getting Help

```bash
# Get help for a specific command
git help [command]

# Quick reference
git [command] --help

# Show Git version
git --version
```

---

## Useful Aliases

Add these to your Git configuration for shortcuts:

```bash
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.st status
git config --global alias.unstage 'reset HEAD --'
git config --global alias.last 'log -1 HEAD'
git config --global alias.lg "log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
```

---

## Common Workflows

### Feature Branch Workflow
```bash
git checkout -b feature-branch
# Make changes
git add .
git commit -m "Add new feature"
git push origin feature-branch
# Create pull request, then after merge:
git checkout main
git pull origin main
git branch -d feature-branch
```

### Fixing a Mistake in Last Commit
```bash
# Make your changes
git add .
git commit --amend --no-edit
git push --force
```

### Syncing a Fork
```bash
git remote add upstream [original-repo-url]
git fetch upstream
git checkout main
git merge upstream/main
git push origin main
```

---

*This cheat sheet covers the most commonly used Git commands. For more detailed information, refer to the [official Git documentation](https://git-scm.com/doc).*
