# Module 05: Merge Conflict Resolution

A merge conflict happens when two diverged branches edit the **same lines** of a file differently. Git pauses the merge and asks a human to choose the final result.


## Part A: The Escape Hatch (`git merge --abort`)

Before solving a conflict, practice backing out safely if a merge surprises you.

1. Start merging the chaotic branch:
   ```bash
   git switch main
   git merge conflict/scary-changes
   ```
2. Git reports `CONFLICT (content)` and pauses. Run `git status` to see `Unmerged paths` (`both modified: modules/05-merge-conflicts/menu.txt`).
3. Bail out completely:
   ```bash
   git merge --abort
   ```
4. Run `git status`—your working tree is completely restored to how it looked right before `git merge`.

---

## Part B: Resolving a Real Conflict

### Step 1: Trigger the conflict
Run:
```bash
git merge conflict/menu-pricing
```
Git stops and tells you `modules/05-merge-conflicts/menu.txt` has a conflict.

### Step 2: Read the conflict markers
Open [menu.txt](menu.txt). Inside, you'll see two conflict blocks structured like this:

```text
<<<<<<< HEAD
Espresso: $3.50
=======
Espresso: $4.00
>>>>>>> conflict/menu-pricing
```

- Everything between `<<<<<<< HEAD` and `=======` is **your current branch (`main`)**.
- Everything between `=======` and `>>>>>>> conflict/menu-pricing` is the **incoming branch**.

<details>
<summary>Tip: VS Code vs. plain text editor</summary>

If you open `menu.txt` in VS Code, you'll see clickable actions above the markers (*Accept Current Change*, *Accept Incoming Change*, *Accept Both Changes*) or a **Resolve in Merge Editor** button. Under the hood, all those buttons do is edit the file and delete the `<<<<<<<`, `=======`, and `>>>>>>>` lines for you!

</details>

### Step 3: Edit `menu.txt` to resolve both conflicts
1. For **Espresso**, pick a final price (for example, compromise on `Espresso: $3.75`, or keep `$3.50` / `$4.00`).
2. For **Seasonal Specials**, keep **both** drinks (`- Honey Oat Latte` and `- Iced Matcha`).
3. **Important:** Delete every `<<<<<<<`, `=======`, and `>>>>>>>` marker line so only clean menu text remains!

### Step 4: Mark resolved and complete the merge
Tell Git you fixed the file by staging it:
```bash
git add modules/05-merge-conflicts/menu.txt
```
Run `git status`—it should now say `All conflicts fixed but you are still merging`.

Finish the merge commit:
```bash
git commit --no-edit
```
*(Or run `git commit` to customize the merge commit message.)*

Inspect your merge commit with `git log --oneline --graph -n 5`, then optionally clean up the merged branch:
```bash
git branch -d conflict/menu-pricing
```

---

**Next:** [Module 06 — Undoing Mistakes & Stashing](../Module-6/README.md)
