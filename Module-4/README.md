# Module 04: Merging (Fast-Forward vs. Three-Way)

Merging integrates commits from another branch into your current branch. Depending on whether the branches have diverged, Git performs either a **Fast-Forward** or a **Three-Way Merge**.


---

## Concepts: Two Types of Merges

```text
1. Fast-Forward (main hasn't moved):      2. Three-Way Merge (both branches moved):
   A ── B ── C ── D  (main, feature)         A ── B ── C ────── M  (main)
                                                       \      /
                                                        E ───┘     (feature)
```

---

## Hands-On Exercise

### Step 1: Inspect the starting branch graph
Run:
```bash
git log --oneline --graph --decorate --all -n 8
```
Notice both `feature/fast-forward` and `feature/three-way` split off from your current `main` commit.

### Step 2: Fast-Forward Merge
Ensure you are on `main`, then merge `feature/fast-forward`:
```bash
git switch main
git merge feature/fast-forward
```
Look at the terminal output—Git prints **`Fast-forward`**. Because `main` had no new commits of its own, Git simply slid the `main` pointer forward!

Check the graph:
```bash
git log --oneline --graph --decorate --all -n 8
```
Notice history is still a straight line with no merge commit.

### Step 3: Three-Way Merge
Because `main` moved forward in Step 2, `main` and `feature/three-way` have now **diverged** (both have commits the other doesn't!).

Merge `feature/three-way` into `main`:
```bash
git merge feature/three-way
```
*(If your text editor opens asking for a merge commit message, save and close it—or run `git merge --no-edit feature/three-way` to accept the default message.)*

Now check the graph and inspect [features.md](features.md):
```bash
git log --oneline --graph --decorate --all -n 8
```
You'll see a diamond shape with a **new merge commit** combining both header updates (`feature/fast-forward`) and footer updates (`feature/three-way`) automatically!

### Step 4: Clean up merged branches
Check which branches have already been merged into `main`:
```bash
git branch --merged
```
Safely delete the merged branches with `-d`:
```bash
git branch -d feature/fast-forward
git branch -d feature/three-way
```

---

**Next:** [Module 05 — Merge Conflict Resolution](../Module-5/README.md)
