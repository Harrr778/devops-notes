# 📦 Git Basics

[[Getting Started]] ← Previous | Next → [[Branches]]

> [!info] Purpose
Learn the **core commands** to track changes in your project.

---

## 🔹 Check Repository Status
```bash
git status
Shows modified, staged, and untracked files

Use often to see what is going on in your repo

🔹 Add Changes

bash

git add file.txt
git add .
git add file.txt → stage specific file

git add . → stage all changes in current directory

🔹 Commit Changes

bash

git commit -m "Fix login bug"
Creates a snapshot of your staged changes

Always write meaningful commit messages

🔹 View History

bash

git log --oneline --graph --all
Shows commit history

--graph → visual tree of branches

--oneline → compact view

[!tip]
Use git diff to see unstaged changes before committing.
Combine git status, git add, and git commit for smooth workflow.