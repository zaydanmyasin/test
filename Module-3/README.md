# Module 03: Branching & Navigation

Branches let you work on features, experiments, or bug fixes in isolation without disturbing `main`.

## Setup for This Module

Run from the repository root:

- **PowerShell:** `.\Module-3\setup\setup.ps1`
- **macOS / Linux / Git Bash:** `/Module-3/setup/setup.sh`

---

## Concepts: Pointers & `HEAD`

A Git branch is simply a **lightweight movable pointer** to a commit, and `HEAD` points to whichever branch you currently have checked out:

```text
  A ── B ── C   (main)
             \
              D  (mystery-clue)  <-- hidden file exists only here!
```

---

## Hands-On Exercise

### Step 1: Discover existing branches
Run:
```bash
git branch -a
```
Notice there is a branch called `mystery-clue` alongside `main`.

### Step 2: Switch to `mystery-clue`
```bash
git switch mystery-clue
```
*(Classic equivalent: `git checkout mystery-clue`)*

List the files inside `modules/03-branching/`—a new file called `clue.txt` has appeared on disk! Open and read `clue.txt` to find the **secret passphrase**.

### Step 3: Switch back to `main`
```bash
git switch main
```
Check `modules/03-branching/` again—`clue.txt` has vanished from your working directory because it only exists on the `mystery-clue` branch!

### Step 4: Create your own feature branch
Create and switch to a new branch called `feature/roadmap-update`:
```bash
git switch -c feature/roadmap-update
```
*(Classic equivalent: `git checkout -b feature/roadmap-update`)*

### Step 5: Commit changes on your new branch
1. Open [roadmap.md](roadmap.md) and replace `<REPLACE_WITH_CLUE>` with the passphrase from `clue.txt` (and mark the checkbox `[x]`).
2. Stage and commit on `feature/roadmap-update`:
   ```bash
   git add modules/03-branching/roadmap.md
   git commit -m "Update roadmap with secret passphrase"
   ```

### Step 6: Watch branches swap file states on disk
Switch back to `main` and open `roadmap.md`:
```bash
git switch main
```
Notice `roadmap.md` still has `<REPLACE_WITH_CLUE>` on `main`! Switch back to `feature/roadmap-update` (`git switch feature/roadmap-update`) to see your update return, then visualize all branches:
```bash
git log --oneline --graph --decorate --all
```
When you're ready for the next module, switch back to `main`:
```bash
git switch main
```

---

**Next:** [Module 04 — Merging](../04-merging/README.md)
