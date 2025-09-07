# 🏋️ Practice (Python DevOps)

[[Configs]] ← Previous

> [!info] Purpose
These examples combine **files, OS automation, network checks, logging, and configs**—everything a DevOps engineer needs in Python scripts.

---

## 🔹 Backup Script
```python
import os
import shutil
from pathlib import Path
import logging

logging.basicConfig(filename="backup.log", level=logging.INFO)

source = Path.home() / "Documents"
backup = Path.home() / "backup"

backup.mkdir(exist_ok=True)

for file in source.glob("*"):
    shutil.copy(file, backup / file.name)
    logging.info(f"Copied {file} to {backup}")

logging.info("Backup completed!")
```

🔹 Server Check Script

```python
import socket
import logging

hosts = ["google.com", "example.com"]
port = 80

logging.basicConfig(filename="network.log", level=logging.INFO)

for host in hosts:
    with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
        result = s.connect_ex((host, port))
        if result == 0:
            logging.info(f"{host}:{port} is reachable")
        else:
            logging.warning(f"{host}:{port} is not reachable")
```

🔹 Config-driven Deployment

```python
import json
import subprocess
import logging

logging.basicConfig(filename="deploy.log", level=logging.INFO)

with open("deploy_config.json") as f:
    config = json.load(f)

server = config["server"]
script = config["script"]

result = subprocess.run(["ssh", server, f"bash -s < {script}"])
if result.returncode == 0:
    logging.info("Deployment succeeded")
else:
    logging.error("Deployment failed")
    ```
    
[!tip]
Combine all modules for real-world automation

Use logging + configs + OS/network modules for robust DevOps scripts

Test scripts on a sandbox environment before running on production