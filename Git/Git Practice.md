# 🏋️ Git Practice

[[Remote Repos]] ← Previous

> [!info] Purpose
Combine all Git commands into **real-world DevOps workflows**: feature branches, commits, merges, and pushing to remote repositories.

---

## 🔹 Feature Branch Workflow
```bash
# Create and switch to a new feature branch
git checkout -b feature/api

# Make changes, add and commit
git add .
git commit -m "Add API integration"

# Merge back to main
git checkout main
git merge feature/api
git branch -d feature/api
Keeps main branch stable

Short-lived branches are easier to manage

🔹 Remote Collaboration

bash

# Push branch to remote
git push -u origin feature/api

# Pull latest changes
git pull origin main

# Fetch remote branches without merging
git fetch
Always pull before pushing to avoid conflicts

Use git log --oneline --graph --all to visualize history

🔹 Hotfix Example

bash

# Create hotfix branch from main
git checkout -b hotfix/security-patch main

# Fix issue, commit, push
git commit -am "Fix security vulnerability"
git push origin hotfix/security-patch

# Merge and delete branch
git checkout main
git merge hotfix/security-patch
git branch -d hotfix/security-patch
[!tip]

Use descriptive commit messages: Add, Fix, Update, Remove

Regularly sync with remote to avoid conflicts

Visualize your branches and merges for clarity