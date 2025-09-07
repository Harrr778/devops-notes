# 🏋️ Bash: Practice Examples

> [!info] Purpose
These examples help you **practice what you learned**: running scripts, variables, functions, loops, and conditions.

---
[[Conditions]] ← Previous
## 🔹 Backup Script
```bash
#!/bin/bash

tar -czf backup.tar.gz ~/Documents
echo "Backup created!"
tar -czf — creates a compressed archive

~/Documents — folder to backup

🔹 CPU Monitoring Script
bash

#!/bin/bash

top -b -n1 | head -5
top -b -n1 — runs top in batch mode, single iteration

head -5 — shows the first 5 lines

🔹 Automatic Package Installation (Debian/Ubuntu)
bash

#!/bin/bash

for pkg in git curl htop; do
    sudo apt install -y $pkg
done
Loops through a list of packages

Installs them automatically without prompts

🔹 Conditional Example
bash

#!/bin/bash

file="/etc/passwd"

if [ -f "$file" ]; then
    echo "$file exists!"
else
    echo "$file does not exist!"
fi
Combines variables, conditions, and echo

[!tip]
Try modifying these scripts:

Add more variables

Use loops for multiple files

Create your own functions
Experimenting is the fastest way to learn Bash!