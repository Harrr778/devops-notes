# 🌿 Branches

[[Git Basics]] ← Previous | Next → [[Remote Repos]]

> [!info] Purpose
Branches allow you to **work on features, fixes, or experiments** without affecting the main codebase.

---

## 🔹 Create a Branch
```bash
git branch feature/login
Creates a new branch called feature/login

🔹 Switch Branch
bash

git checkout feature/login
# or in newer Git versions
git switch feature/login
Moves your working directory to the branch

🔹 Merge Branch
bash

git checkout main
git merge feature/login
Merges feature/login into main

Resolve conflicts if they appear

🔹 Delete Branch
bash

git branch -d feature/login
Deletes local branch after merging

Use -D to force delete if not merged

[!tip]

Keep main branch clean and stable

Work on short-lived feature branches

Use descriptive names: feature/*, bugfix/*, hotfix/*