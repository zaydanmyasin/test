# Module 02: `.gitignore` & `.gitkeep`

Not everything belongs in Git. Build outputs, log files, OS metadata, and `.env` secrets should stay out of version control—while empty placeholder folders (like `uploads/` or `logs/`) sometimes need to be kept in the repository structure.

**NOTE** `.env` file is a plain text file used to store environment-specific configuration and sensitive data like API keys, database URLs, and secret tokens.

## Part A: Ignore Patterns, Negation & `git check-ignore`
### Step 1: Create temporary files that shouldn't be committed

**RUN IN THE REPOSITORY ROOT DIRECTORY**<br>
**Windows: PowerShell:**
```powershell
New-Item -ItemType Directory -Force Module-2/temp | Out-Null
"debug output" | Out-File Module-2/debug.log
"critical audit log" | Out-File Module-2/important.log
"cache data" | Out-File Module-2/temp/cache.tmp
```

**macOS / Linux: Bash:**
```bash
mkdir -p Module-2/temp
echo "debug output" > Module-2/debug.log
echo "critical audit log" > Module-2/important.log
echo "cache data" > Module-2/temp/cache.tmp
```

Running `git status` shows lists all three as untracked files

### Step 2: Update the root `.gitignore`
Open `.gitignore` at the repository root and add.
```gitignore
*.log
!important.log
temp/
```
**---DO NOT FORGET TO SAVE---**

Now check what Git sees:
```bash
git status
git status --ignored
git check-ignore -v modules/02-ignoring-and-keeping/debug.log
```
**NOTICE** 
- `debug.log` and `temp/` are ignored.
- `important.log` is **still visible** because `!important.log` negates the `*.log` rule!
- `git check-ignore -v` tells you the exact file and line number causing a path to be ignored.

*(Clean up `Module-2/important.log` or commit it before continuing so it doesn't stay untracked later.)*

---

## Part B: Untracking an Already-Committed File (`git rm --cached`)
> **Key Rule:** `.gitignore` only ignores **untracked** files. If a file was already committed, Git continues tracking changes to it!

Look at [accidentally-tracked.env](accidentally-tracked.env), it is already committed in this repository.
1. Edit `Module-2/accidentally-tracked.env` and change `APP_ENV=development` to `APP_ENV=local`.
2. Add `*.env` to your root `.gitignore`.
3. Run `git status`. **NOTICE** `accidentally-tracked.env` still shows up in `modified:`!
4. Remove it from Git's index **without deleting it from your disk**:
   ```bash
   git rm --cached Module-2/accidentally-tracked.env
   ```
5. Run `git status` and check that the file is still in the folder on disk. Now commit your `.gitignore` and the untracking change:
   ```bash
   git add .gitignore
   git commit -m "Ignore .env files and untrack accidentally-tracked.env"
   ```
---

## Part C: Keeping Empty Directories with `.gitkeep`
1. Create an empty directory:
   ```bash
   mkdir modules/02-ignoring-and-keeping/uploads
   ```
2. Run `git status`. Git shows **nothing**—an empty directory cannot be added or committed.
3. Create an empty `.gitkeep` file inside `uploads/`:
   - **PowerShell:** `New-Item -ItemType File Module-2/uploads/.gitkeep`
   - **Bash:** `touch Module-2/uploads/.gitkeep`
4. Now configure `.gitignore` so the `uploads/` folder stays in Git via `.gitkeep`, while any real files put inside `uploads/` are ignored:
   ```gitignore
   Module-2/uploads/*
   !Module-2/.gitkeep
   ```
   > **Why `uploads/*` instead of `uploads/`?** If you ignore a parent directory (`uploads/`), Git never enters it, so `!uploads/.gitkeep` won't work. Using `uploads/*` ignores its contents while still letting `!uploads/.gitkeep` match.

5. Test it! Create a dummy file `Module-2/uploads/juan.txt` and run `git status`. Only `.gitignore` and `uploads/.gitkeep` appear; `juan.txt` is ignored!
6. Stage and commit `.gitignore` and `uploads/.gitkeep`:
   ```bash
   git add .gitignore Module-2/uploads/.gitkeep
   git commit -m "Keep uploads directory with .gitkeep while ignoring contents"
   ```

---

**Next:** [Module 03 — Branching](../Module-3/README.md)