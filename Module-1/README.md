# Module 01: Basics Commands & Git Trees
In this module, you will practice the core Git daily workflow and learn why Git separates editing files, staging changes, and committing snapshots.

## Common Terms
- Repository (Repo): A storage folder that holds all of your project files along with their complete revision history
- Commit: A permanent snapshot of your staged changes at a specific point in time, paired with a short message describing what you updated
- Branch: An independent, parallel line of development that lets you build features or test ideas without affecting the main codebase
- Main: The default primary branch in a repository that typically holds the stable, production-ready version of your project
- Merge: The process of combining changes from one branch into another
- Stage/Staging: the process of selecting and preparing specific file changes to be included in your next commit

## The Three Trees
The Three Trees in Git are the core mental model for how Git manages and tracks your project files. In this context, a "tree" simply refers to a collection of files and directories representing a specific snapshot of your project. 

1. Working Directory (Working Tree): This is the actual folder on your computer where you view, create, and edit files in your code editor.
2. Index (Staging Area): This is a temporary draft zone stored inside the .git folder that holds the exact snapshot of changes you plan to include in your next commit.
3. HEAD (Commit History): This is a pointer to the last commit on your currently checked-out branch

```text
    Working Directory --(git add)--> Staging Area --(git commit) --> Repository (HEAD)4
       [Edit Files]               [Pick what to commit]               [saved commits]
```

## Hands-On

### Step 1: Check Current Repository State
```
git status
```

You should see something along the lines of 
```text
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
```

### Step 2: Edit both files in this folder
1. Open [notes.txt](notes.txt) and replace `(Add your first note here during Module 01)` with a the explanation of The Three Trees
2. Open [todo.md](todo.md) and check off the first two items (`[x]`).

### Step 3: Stage only ONE file 
Stage **only** `notes.txt`:
```bash
git add Module-1/notes.txt
```
Now run and compare the outputs
```bash
git diff
git diff --staged
```
- `git diff` shows **unstaged** changes (`todo.md`).
- `git diff --staged` shows **staged** changes (`notes.txt`) that will go into your next commit.

### Step 4: Make two separate atomic commits
Commit the staged `notes.txt` change first:
```bash
git commit -m "Staged Note.txt"
```
**Notice:** Running `git status` reveals that `Module-1/todo.md` is untracked, meaning git isn't monitoring its changes
```text
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        Module-1/todo.md
```
To change that, we stage it.
```bash
git add Module-1/todo.md
git commit -m "Complete Module 01 checklist"
```

### Step 5: Inspect your history
```bash
git log --oneline -n 5
git show HEAD
```

### Step 6: Pushing Changes to Repository
So far, we've only recorded the commits locally, meaning other people won't be able to see the changes that we've made so far. To change that we push the changes to the repository by running
```bash
git push origin main
```
You should see two clean, separate commits at the top of your history and a clean working tree in `git status`.


---
**NEXT** [Module-02](../Module-2/README.md)