# 🌐 Network (Python DevOps)

[[Logging]] ← Previous | Next → [[Configs]]

> [!info] Purpose
Network checks and HTTP requests are essential for **monitoring servers, APIs, and services** in DevOps.

---

## 🔹 Check if host and port are reachable
```python
import socket

host = "google.com"
port = 80

with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
    result = s.connect_ex((host, port))
    if result == 0:
        print(f"{host}:{port} is reachable")
    else:
        print(f"{host}:{port} is not reachable")
```

connect_ex() returns 0 if successful

🔹 Simple HTTP request
```python
import requests

response = requests.get("https://api.github.com")
if response.status_code == 200:
    print("GitHub API is up!")
else:
    print("Failed to reach GitHub API")
requests library is simple and reliable for REST APIs

Always check status_code
```


[!tip]
Use network checks in automation scripts to verify services before deploying or running jobs.