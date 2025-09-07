# 🌐 Remote Repos

[[Branches]] ← Previous | Next → [[Git Practice]]

> [!info] Purpose
Remote repositories allow you to **collaborate with teams** and keep your code backed up.

---

## 🔹 Add Remote
```bash
git remote add origin https://github.com/user/repo.git
origin is the default remote name

Can add multiple remotes if needed

🔹 Push Changes
bash

git push -u origin main
-u sets upstream branch

After first push, git push is enough

🔹 Pull Changes
bash

git pull origin main
Fetches and merges changes from remote

🔹 Fetch Changes
bash

git fetch
Updates remote branches without merging

[!tip]

Use git remote -v to see configured remotes

Always pull before pushing to avoid conflicts