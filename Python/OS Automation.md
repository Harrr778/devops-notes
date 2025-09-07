# 🛠 OS Automation (Python DevOps)

[[Python/Running]] ← Previous | Next → [[Path Handling]]

> [!info] Purpose
Python allows you to **automate file operations, system commands, and folder management**, which is crucial in DevOps.

---

## 🔹 Working with Files and Directories (`os`, `shutil`)
```python
import os
import shutil

# Check if a folder exists
if not os.path.exists("backup"):
    os.mkdir("backup")

# Copy a file
shutil.copy("config.yaml", "backup/config.yaml")

# Remove a folder
# shutil.rmtree("backup")
🔹 Running System Commands (subprocess)

import subprocess

# Run a simple command
result = subprocess.run(["ls", "-l"], capture_output=True, text=True)
print(result.stdout)

# Check exit code
if result.returncode == 0:
    print("Command succeeded")
```
capture_output=True captures stdout and stderr

text=True returns output as string

🔹 Best Practices

Always handle exceptions (try/except)

Use absolute paths when automating scripts for servers

Avoid os.system() for critical tasks—use subprocess.run

[!tip]
Combine os + shutil + subprocess to create automated deployment, backup, or monitoring scripts.