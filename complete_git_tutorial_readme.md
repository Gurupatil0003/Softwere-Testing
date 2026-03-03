# 🚀 COMPLETE GIT TUTORIAL (BEGINNER TO ADVANCED)

---

# 1️⃣ Git Setup (One-Time Configuration)

```bash
git --version
```

```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
```

Check configuration:

```bash
git config --list
```

---

# 2️⃣ Create & Initialize Repository

```bash
mkdir project-name
cd project-name
git init
```

Check hidden files:

```bash
ls -a
```

---

# 3️⃣ Basic Workflow (Add → Commit → Log)

Check status:

```bash
git status
```

Add specific file:

```bash
git add filename.py
```

Add all files:

```bash
git add .
```

Commit changes:

```bash
git commit -m "Your commit message"
```

View commit history:

```bash
git log
```

Short history:

```bash
git log --oneline
```

---

# 4️⃣ View Changes

See file differences:

```bash
git diff
```

See staged differences:

```bash
git diff --staged
```

---

# 5️⃣ Branching

List branches:

```bash
git branch
```

Create branch:

```bash
git branch branch-name
```

Switch branch:

```bash
git checkout branch-name
```

Modern switch:

```bash
git switch branch-name
```

Create & switch:

```bash
git checkout -b branch-name
```

Delete branch:

```bash
git branch -d branch-name
```

---

# 6️⃣ Merging

Switch to main branch:

```bash
git checkout main
```

Merge branch:

```bash
git merge branch-name
```

Abort merge:

```bash
git merge --abort
```

---

# 7️⃣ Undo Changes

Unstage file:

```bash
git restore --staged filename
```

Discard changes in file:

```bash
git restore filename
```

Reset last commit (keep changes):

```bash
git reset --soft HEAD~1
```

Reset last commit (delete changes):

```bash
git reset --hard HEAD~1
```

Reset specific commit:

```bash
git reset --hard commit-id
```

---

# 8️⃣ Stashing (Temporary Save)

Save current work:

```bash
git stash
```

List stashes:

```bash
git stash list
```

Apply stash:

```bash
git stash apply
```

Apply & remove stash:

```bash
git stash pop
```

Delete stash:

```bash
git stash drop
```

---

# 9️⃣ Remote Repository (GitHub)

Add remote:

```bash
git remote add origin https://github.com/username/repository.git
```

View remotes:

```bash
git remote -v
```

Rename branch to main:

```bash
git branch -M main
```

Push first time:

```bash
git push -u origin main
```

Push changes:

```bash
git push
```

Pull changes:

```bash
git pull
```

Fetch changes:

```bash
git fetch
```

Remove remote:

```bash
git remote remove origin
```

---

# 🔟 Clone Repository

```bash
git clone https://github.com/username/repository.git
```

Clone specific branch:

```bash
git clone -b branch-name https://github.com/username/repository.git
```

---

# 1️⃣1️⃣ Rebase (Advanced)

Rebase current branch:

```bash
git rebase main
```

Interactive rebase:

```bash
git rebase -i HEAD~3
```

Abort rebase:

```bash
git rebase --abort
```

---

# 1️⃣2️⃣ Cherry-Pick

Apply specific commit:

```bash
git cherry-pick commit-id
```

---

# 1️⃣3️⃣ Tagging (Versioning)

Create tag:

```bash
git tag v1.0
```

Create annotated tag:

```bash
git tag -a v1.0 -m "Version 1.0"
```

Push tags:

```bash
git push origin --tags
```

List tags:

```bash
git tag
```

---

# 1️⃣4️⃣ .gitignore Example (Python Project)

```
__pycache__/
*.pyc
.env
venv/
db.sqlite3
.idea/
.vscode/
```

---

# 1️⃣5️⃣ Useful Logs & Inspection

Graph log:

```bash
git log --oneline --graph --all
```

Show commit details:

```bash
git show commit-id
```

Who changed what:

```bash
git blame filename.py
```

---

# 1️⃣6️⃣ Remove Files

Remove file from Git:

```bash
git rm filename
```

Remove but keep locally:

```bash
git rm --cached filename
```

---

# 1️⃣7️⃣ Clean Untracked Files

Remove untracked files:

```bash
git clean -f
```

Remove untracked directories:

```bash
git clean -fd
```

---

# 1️⃣8️⃣ Full Professional Workflow

```bash
git checkout -b feature-login
git add .
git commit -m "Added login feature"
git push -u origin feature-login
```

After PR merge:

```bash
git checkout main
git pull
git branch -d feature-login
```

---

# 📌 Golden Rules

- Always `git pull` before pushing
- Never push directly to `main`
- Write meaningful commit messages
- Keep commits small
- Use feature branches

---

# 🔥 Most Used Commands (Quick Revision)

```bash
git init
git add .
git commit -m "message"
git status
git log --oneline
git branch
git checkout -b branch-name
git merge branch-name
git pull
git push
git stash
git reset --soft HEAD~1
```

