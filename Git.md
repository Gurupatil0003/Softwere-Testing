```python
from selenium import webdriver
from selenium.webdriver.common.by import By
import os
import time

# Start browser
driver = webdriver.Chrome()
driver.maximize_window()

# Open iLovePDF PDF to Word tool
driver.get("https://www.ilovepdf.com/pdf_to_word")

time.sleep(3)

# Get absolute path of PDF
file_path = os.path.abspath("sample.pdf")  # Make sure this exists

# Find file upload input
file_input = driver.find_element(By.XPATH, "//input[@type='file']")

# Upload PDF
file_input.send_keys(file_path)

print("Uploading PDF...")

time.sleep(5)

# Click Convert button
convert_btn = driver.find_element(By.ID, "processTask")
convert_btn.click()

print("Converting to Word...")

time.sleep(10)

# Click Download button
download_btn = driver.find_element(By.XPATH, "//a[contains(@class,'download')]")
download_btn.click()

print("Download started!")

time.sleep(5)

driver.quit()
```

# 📘 Complete Git Command Reference Guide

A structured list of essential Git commands with explanations.

---

# 1️⃣ Git Configuration

## Set Username
git config --global user.name "Your Name"  
Sets your global Git username.

## Set Email
git config --global user.email "your@email.com"  
Sets your global Git email.

## View Configuration
git config --list  
Displays all Git configuration settings.

## Set Default Branch Name
git config --global init.defaultBranch main  
Sets default branch to `main`.

---

# 2️⃣ Repository Setup

## Initialize Repository
git init  
Creates a new Git repository in the current directory.

## Clone Repository
git clone https://github.com/username/repository-name.git  
Downloads a remote repository to your local system.

---

# 3️⃣ Check Repository Status

## Check Status
git status  
Shows modified, staged, and untracked files.

## View Commit History
git log  
Displays detailed commit history.

## Compact Commit History
git log --oneline  
Shows one-line summary per commit.

## Graph View
git log --graph --decorate  
Shows commit tree graph.

## See Changes
git diff  
Shows changes not staged yet.

## See Staged Changes
git diff --staged  
Shows staged changes.

## View Specific Commit
git show commit_id  
Displays detailed information about a commit.

---

# 4️⃣ Staging & Committing

## Stage Specific File
git add filename  

## Stage All Files
git add .  

## Commit Changes
git commit -m "commit message"  

## Amend Last Commit
git commit --amend  
Modifies the most recent commit.

---

# 5️⃣ Undo & Restore

## Discard Changes in File
git restore filename  

## Unstage File
git restore --staged filename  

## Soft Reset
git reset --soft commit_id  
Keeps changes staged.

## Mixed Reset
git reset --mixed commit_id  
Unstages changes but keeps them.

## Hard Reset
git reset --hard commit_id  
Deletes all changes permanently.

## Revert Commit
git revert commit_id  
Creates new commit reversing changes.

## Remove Untracked Files
git clean -f  

## Remove Untracked Files & Folders
git clean -fd  

---

# 6️⃣ Branching

## List Branches
git branch  

## Create Branch
git branch branch-name  

## Delete Branch
git branch -d branch-name  

## Force Delete Branch
git branch -D branch-name  

## Switch Branch
git checkout branch-name  

## Create & Switch Branch
git checkout -b branch-name  

## Modern Switch
git switch branch-name  

## Create & Switch (Modern)
git switch -c branch-name  

---

# 7️⃣ Merge & Rebase

## Merge Branch
git merge branch-name  

## Rebase Branch
git rebase branch-name  

## Continue Rebase
git rebase --continue  

## Abort Rebase
git rebase --abort  

---

# 8️⃣ Remote Commands

## View Remotes
git remote -v  

## Add Remote
git remote add origin https://github.com/username/repository-name.git  

## Remove Remote
git remote remove origin  

## Fetch Changes
git fetch origin  

## Pull Changes
git pull origin main  

## Push Changes
git push origin main  

## Push & Set Upstream
git push -u origin main  

## Push Specific Branch
git push origin branch-name  

## Force Push
git push --force origin branch-name  

---

# 9️⃣ Stashing

## Save Changes
git stash  

## List Stashes
git stash list  

## Apply Stash
git stash apply  

## Apply & Remove Stash
git stash pop  

## Delete Specific Stash
git stash drop stash@{0}  

## Clear All Stashes
git stash clear  

---

# 🔟 Tags

## List Tags
git tag  

## Create Tag
git tag tag-name  

## Annotated Tag
git tag -a tag-name -m "message"  

## Push Tag
git push origin tag-name  

## Push All Tags
git push origin --tags  

## Delete Tag
git tag -d tag-name  

---

# 1️⃣1️⃣ Inspection & Debugging

## Blame
git blame filename  
Shows who modified each line.

## Reflog
git reflog  
Shows HEAD movement history.

## Shortlog
git shortlog  
Summary of commits by author.

## Describe
git describe --tags  
Shows nearest tag for commit.

---

# 🚀 Daily Workflow Example

git clone repository-url  
git checkout -b feature-branch  
git add .  
git commit -m "Added feature"  
git push -u origin feature-branch  

---

# ⭐ Top 10 Most Used Commands

git status  
git add .  
git commit -m "message"  
git push  
git pull  
git branch  
git checkout -b branch-name  
git merge branch-name  
git stash  
git log --oneline  

---

# 📌 End of Git Reference

# Git Branch Visualization Example



# Git Graph Example with Left and Right Branches

This example demonstrates how to create **left and right branches** and visualize them using **Git Graph in VS Code**.

---

# Step-by-Step Commands

## 1️⃣ Start Repository

```bash
git init

echo "start" > v.py
git add .
git commit -m "c1 start"
```

---

## 2️⃣ Create LEFT Branch

```bash
git switch -c feature-left

echo "left work" >> v.py
git add .
git commit -m "c2 left work"
```

---

## 3️⃣ Back to Master and Create RIGHT Branch

```bash
git switch master
git switch -c feature-right

echo "right work" > a.py
git add .
git commit -m "c3 right work"
```

---

## 4️⃣ Create Small Branch from Right

```bash
git switch -c small-fix

echo "small fix" >> a.py
git add .
git commit -m "c4 small fix"
```

---

## 5️⃣ Merge Small Branch into Right Branch

```bash
git switch feature-right
git merge small-fix
```

---

## 6️⃣ Merge Branches into Master

```bash
git switch master
git merge feature-left
git merge feature-right
```

---

# Git Graph Structure

```
*   Merge feature-right
|\
| * small-fix
| * feature-right
|/
*   Merge feature-left
|\
| * feature-left
|/
* c1 start
```

In **VS Code Git Graph extension**, this will appear as a **colorful graph with left and right branches**.

---

# ⭐ Pro Tip (Better Looking Graph)

Add one more commit before merging to make the branch lines **longer and clearer**.

```bash
git commit -m "update feature"
```

---

# View Graph in VS Code

Open **Command Palette**

```
Ctrl + Shift + P
```

Search:

```
Git Graph: View Git Graph
```


This guide shows how to create a **left-side branch (green line)** in the Git graph.

---

## 1️⃣ Start Repository (Commits A → B)

```bash
git init

echo "A" > v.py
git add .
git commit -m "A"

echo "B" >> v.py
git commit -am "B"
```

---

## 2️⃣ Create Left Branch from Commit A

This creates the **left branch (green line)** in the Git graph.

```bash
git switch -c left-branch HEAD~1

echo "left work" >> v.py
git commit -am "left branch work"
```

---

## 3️⃣ Go Back to Main Branch and Continue

```bash
git switch master

echo "C" >> v.py
git commit -am "C"
```

---

## 4️⃣ Merge Left Branch

```bash
git merge left-branch
```

---

## 5️⃣ View Git Graph in VS Code

Open **Command Palette**

```
Ctrl + Shift + P
```

Search for:

```
Git Graph: View Git Graph
```

---

## Expected Git Graph

```
      left branch work
           /
A --- B --- C
           \
            merge
```

