# GIT CHEATSHEET

## Table of Contents
1. [Basic Commands](#basic-commands)
2. [Special Git Config Files](#special-git-config-files)


## Basic Commands

### Start or Clone Repository

| Command | Function |
| :--- | :--- |
| `git init` | Turns current folder into a git repository |
| `git clone <url>` | Donwloads an existing repository from github | 

### Check Status & History

| Command | Function | 
| :--- | :--- | 
| `git status` | Show current branch and staged, modified, and untracked files | 
| `git diff` | View unstaged changes line by line | 
| `git diff --staged` | View staged changes ready for the next commit | 
| `git log --oneline --n 10` | Show the last 10 commits of a branch in compact form |
| `git log ---oneline --graph --all` | Show branch and merge history visually |

### Stage & Commit Changes

| Command | Function | 
| :--- | :--- |
| `git add <file>` <br> `git add /path/to/file` | Stage a specific file for commit |
| `git add .` | Stage all new, modified, and deleted files in the current directory |
| git commit -m "Message" | Save staged changes as a new commit |

### Branching & Merging

| Command | Function |
| :--- | :--- |
| `git branch` | List local branches (use `-a` to include remote branches) |
| `git switch <branch>` | Switch to an existing branch (legacy: `git checkout <branch>`) | 
| `git switch -c <new-branch>` | Create and switch to a new branch (legacy: `git checkout -b <new-branch>`) |
| `git merge <branch>` | Merge `<branch> `into your currently active branch | 
| `git merge --abort ` | Safely cancels an in-progress merge and restores your repository to its exact state before the merge started |
| `git branch -d <branch>` | Delete a merged local branch (`-D` force-deletes an unmerged branch) | 

### Synch with Github
| Command | Function |
| :--- | :--- |
| `git fetch` | Download remote updates without changing your local files |
| `git pull` | Fetch remote changes and merge/rebase them into the current branch |
| `git push -u origin <branch>` | Push a branch for the first time and link it to `origin` |
| `git push` | Push local commits to the linked remote branch |

### Stash & Undo
| Command | Function |
| :--- | :--- |
| `git stash` | Temporarily set aside uncommitted changes to get a clean working tree |
| `git stash pop` | Re-apply the most recent stash and remove it from the stash list | 
| `git restore --staged <file>` | Unstage a file while keeping its edits on disk |
| `git restore <file>`| Discard unstaged local edits to a file |
| `git revert <commit>` |Create a new commit that reverses an earlier commit (safe for shared/pushed history) |
| `git reset --soft HEAD~1` | Undo the last local commit while keeping changes staged |  

## Git Typical Daily Cycle
```bash
git pull # Get latest changes from GitHub
git switch -c feat/my-task # Create a working branch
git add . # Stage Changes
git commit -m "Add feature" # Commit Locally
git push origin feat/my-task # Push changes to github
git switch main # Switch to main
git pull # Get Latest Main Version
git switch feat/my-task # Switch to branch feat/my-task
git merge main # Merges main to current branch
# <Resolve merge conflicts>
git push # Push changes to branch
git switch main # Switch to main
git merge feat/my-task # Merge changes from feat/my-task to main
```

## Special Git Config Files
Details of files used for git repository configurations and more
1. `.gitignore`

    `.gitignore` is an official Git configuration file that tells Git which files or folders to exclude from version control. This means anything listed inside of the `.gitignore` won't be pushed to the repository. This is useful for sensitive files such as `.env` and OS clutter files like `.DS_Store`

2. `.gitkeep`

    `.gitkeep` is a community convention used to force Git to track empty folders. Git won't track empty folders, so the community devised this convention to force git to track empty folders.