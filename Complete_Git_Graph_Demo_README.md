# 🚀 Complete Git Graph Demonstration Project

## Using VS Code Git Graph Extension

This project demonstrates a full Git workflow including:

-   Repository Initialization
-   Branch Creation
-   Multiple Commits
-   Feature Development
-   Hotfix Workflow
-   Merging
-   Graph Visualization

------------------------------------------------------------------------

# 📌 1️⃣ Project Setup

## Create New Project Folder

``` bash
mkdir git-graph-demo
cd git-graph-demo
git init
```

------------------------------------------------------------------------

# 📌 2️⃣ Initial Commit (Main Branch)

``` bash
echo "Project Started" > app.txt
git add .
git commit -m "Initial commit"
```

------------------------------------------------------------------------

# 📌 3️⃣ Create Feature Branch

``` bash
git switch -c feature-authentication
```

------------------------------------------------------------------------

# 📌 4️⃣ Add Multiple Commits in Feature Branch

``` bash
echo "Login UI Created" >> app.txt
git commit -am "Added login UI"

echo "Login Backend Logic Added" >> app.txt
git commit -am "Added login backend logic"

echo "JWT Authentication Added" >> app.txt
git commit -am "Implemented JWT authentication"
```

------------------------------------------------------------------------

# 📌 5️⃣ Switch Back to Main Branch

``` bash
git switch master
```

------------------------------------------------------------------------

# 📌 6️⃣ Add Commit in Main Branch

``` bash
echo "Homepage Updated" >> app.txt
git commit -am "Updated homepage design"
```

------------------------------------------------------------------------

# 📌 7️⃣ Merge Feature Branch

``` bash
git merge feature-authentication
```

------------------------------------------------------------------------

# 📌 8️⃣ Create Hotfix Branch

``` bash
git switch -c hotfix-payment-bug
echo "Fixed payment calculation bug" >> app.txt
git commit -am "Critical payment bug fix"

git switch master
git merge hotfix-payment-bug
```

------------------------------------------------------------------------

# 📌 9️⃣ Optional: Create Dashboard Feature

``` bash
git switch -c feature-dashboard
echo "Dashboard UI Added" >> app.txt
git commit -am "Added dashboard UI"

echo "Dashboard API Integrated" >> app.txt
git commit -am "Integrated dashboard API"

git switch master
git merge feature-dashboard
```

------------------------------------------------------------------------

# 📊 View Graph in VS Code

1.  Open VS Code\
2.  Press Ctrl + Shift + P\
3.  Search: Git Graph: View Git Graph\
4.  Open it

------------------------------------------------------------------------

# 🖥 Terminal Graph View

``` bash
git log --graph --oneline --all --decorate
```

------------------------------------------------------------------------

# 🎯 Concepts Covered

-   Git initialization
-   First commit requirement
-   Branch creation
-   Switching branches
-   Commit divergence
-   Merge commits
-   Hotfix workflow
-   Professional branching structure
-   Graph visualization

------------------------------------------------------------------------

# ✅ End of Complete Git Graph Guide
