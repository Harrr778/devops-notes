# 🐍 Running Python Scripts (DevOps)

Next → [[OS Automation]]

> [!info] What is Python for DevOps?
Python is widely used in DevOps for **automation, monitoring, and deployment scripts**.  
You don’t need GUI or heavy frameworks—just scripts that run reliably on servers.

---

## 🔹 Shebang for Linux Scripts
```python
#!/usr/bin/env python3
Place it at the top of your script to make it executable in Linux.

Run directly:

bash

chmod +x deploy.py
./deploy.py
```

🔹 Virtual Environments

```bash
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

Keeps dependencies isolated

Recommended for every project

🔹 Running Scripts

```bash
python3 script.py
```

Works in any terminal

Use python3 -m module_name for modules

[!tip] For long-running DevOps scripts, consider adding logging and error handling to make them reliable.