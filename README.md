# Git Commands Cheat Sheet

A concise and practical reference for essential Git commands.  
This repository covers Git setup, configuration, commits, branching, stashing, merging, undoing changes, and help utilities.

---

## Prerequisites

- Git installed on your system
- Terminal / Git Bash / Command Prompt

Check Git installation:
```bash
git --version
```

---

## Git Configuration

### Set Global Username and Email

```bash
git config --global user.name "Your Name"
git config --global user.email "email@example.com"
```

### Set Email for Current Repository Only

```bash
git config --local user.email "email@example.com"
```

**Notes:**
- Use global config for personal machines.
- Use local config when working with multiple Git accounts.

---

## Repository Setup & First Commit

### Initialize a Repository

```bash
git init
```

### Check Repository Status

```bash
git status
```

### Create a Commit

```bash
git commit -m "Initial commit"
```

### Stage All Modified & Deleted Files, Then Commit

```bash
git commit -a -m "Commit message"
```

### View Commit History

```bash
git log
```

---

## Commit Message Editor & Amend

### Open Editor for Multi-line Commit Message

```bash
git commit
```

### Reuse Previous Commit Message

```bash
git commit --no-edit
```

### Amend Last Commit (Change Message) / want to edit. the prev commit msg

```bash
git commit --amend -m "Updated commit message"
```

### Amend Without Changing Message

```bash
git commit --amend --no-edit
```

**⚠️ Warning:** Amending rewrites history. Avoid using it on commits already pushed to shared branches.

---

## Viewing Commit Details

### Compact Commit History

```bash
git log --oneline
```

### Commit Statistics

```bash
git log --stat
```

---

## Staging & Unstaging Files

### Stage Files

```bash
git add <file>
git add .
```

### Unstage a File

```bash
git reset <file>
```

---

## Stash Workflow

### Save Current Changes

```bash
git stash
```

### Save Changes With a Message (Recommended)

```bash
git stash push -m "WIP: add login form"
```

### List Stashes

```bash
git stash list
```

### Apply a Stash (Keep It)

```bash
git stash apply stash@{0}
```

### Apply and Remove Stash

```bash
git stash pop
```

### Create a Branch From a Stash

```bash
git stash branch feature-branch stash@{0}
```

---

## Stash Cleanup

### Drop a Specific Stash

```bash
git stash drop stash@{2}
```

### Clear All Stashes

```bash
git stash clear
```

**⚠️ Warning:** Stash clear is permanent and cannot be undone.

---

## Branching

### Create a Branch

```bash
git branch feature/login
```

### Switch Branch

```bash
git checkout feature/login
```

### Create & Switch (Legacy Syntax)

```bash
git checkout -b feature/login
```

### Create & Switch (Modern Syntax)

```bash
git switch -c feature/login
```

---

## Merging Branches

### Merge a Feature Branch

```bash
git merge feature-branch
```

### Squash Merge (Single Commit)

```bash
git merge --squash feature-branch
git commit
```

### Abort a Failed Merge

```bash
git merge --abort
```

---

## Working With Remotes

### Add a Remote Repository

```bash
git remote add origin https://github.com/username/repo.git
```

### Change Remote URL

```bash
git remote set-url origin https://github.com/username/new-repo.git
```

### Fetch All Remotes

```bash
git fetch --all
```

---

## Undoing Changes

### Revert Commits (Safe for Shared History)

```bash
git revert <commit_id>
git revert HEAD
git revert HEAD~2
```

### Reset Commits (Dangerous)

```bash
git reset --soft <commit>    # Keep staged changes
git reset --mixed <commit>   # Unstage changes (default)
git reset --hard <commit>    # Discard all changes
```

### Undo Last Commit but Keep Changes

```bash
git reset --mixed HEAD~1
```

**⚠️ Warning:** Never use `git reset --hard` on pushed commits unless you fully understand the consequences.

**Notes:**
- `git revert` creates a new commit that reverses the effect of a previous commit. This is the safe option for undoing changes already pushed to a shared remote.
- `git reset` rewrites history and should not be used on commits that have been pushed to a shared branch unless you understand the implications.
- Prefer `git revert` over `git reset` on shared branches.

---

## Help & Documentation

### List All Git Commands

```bash
git help --all
```

### View Command Groups

```bash
git help -g
```

---

## Best Practices

- **Write clear and meaningful commit messages** — describe what changed and why.
- **Prefer `git revert` over `git reset` on shared branches** — preserves history for collaborators.
- **Use `git status` frequently** — stay aware of staged and unstaged changes.
- **Always stash with descriptive messages** — `git stash push -m "description"` is better than `git stash`.
- **Fetch before pushing** — `git fetch --all` then review before pushing changes.
- **Check `git log --oneline` before important operations** — verify you're on the right commit.

---

**Last Updated:** January 16, 2026
