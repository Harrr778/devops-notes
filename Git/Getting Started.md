# 🐙 Getting Started with Git

Next → [[Git Basics]]

> [!info] What is Git?
Git is a **distributed version control system**.  
It allows you to **track changes, collaborate, and manage code** efficiently.

---

## 🔹 Install Git
```bash
# Debian/Ubuntu
sudo apt install git

# Fedora
sudo dnf install git

# Arch
sudo pacman -S git
🔹 Configure Git

bash

git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git config --global color.ui auto
Sets your identity for commits

Enables colored output for easier reading

🔹 Create or Clone Repository

bash

# Clone existing repo
git clone https://github.com/user/repo.git

# Initialize new repo
git init my_project
cd my_project
[!tip]
Always check your Git version:

bash

git --version
Keep your Git up-to-date for the latest features and security fixes.