# 🛤 Path Handling (Python DevOps)

[[OS Automation]] ← Previous | Next → [[Logging]]

> [!info] Purpose
Using **pathlib** makes file and directory handling **cross-platform** and cleaner than using `os.path`.

---

## 🔹 Working with Paths
```python
from pathlib import Path

# Current directory
cwd = Path.cwd()
print(cwd)

# Home directory
home = Path.home()
print(home)

# Join paths
config_path = home / "config" / "settings.yaml"
print(config_path)
🔹 Check if file or folder exists
python
Copy code
if config_path.exists():
    print("Config file exists!")
else:
    print("Config file not found!")
.is_file() → True if path is a file

.is_dir() → True if path is a directory
```

🔹 Create directories safely

```python
backup_dir = Path("backup")
backup_dir.mkdir(exist_ok=True)
exist_ok=True avoids errors if folder already exists
```

[!tip]
Always use pathlib for DevOps scripts instead of os.path.join—it’s safer and readable.