# 🖥 Network Practice (DevOps)

[[Security]] ← Previous

> [!info] Purpose
Practice network commands and automation scripts to **monitor, test, and troubleshoot** servers and networks.  
Combines Bash and Python examples for DevOps workflows.

---

## 🔹 Basic Host Checks
**Ping a host:**
```bash
ping -c 4 google.com
```

Check connectivity to multiple hosts (Bash loop):

```bash
hosts=("google.com" "github.com" "example.com")
for host in "${hosts[@]}"; do
    if ping -c 1 $host &> /dev/null; then
        echo "$host is reachable"
    else
        echo "$host is down"
    fi
done
```

## 🔹 Port Checks

**Check if a port is open (Bash):**

```
nc -zv 192.168.1.10 22
```

Python TCP port check:

```python 
import socket

hosts = ["example.com"]
port = 22

for host in hosts:
    with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
        result = s.connect_ex((host, port))
        if result == 0:
            print(f"{host}:{port} is reachable")
        else:
            print(f"{host}:{port} is down")

```

## 🔹 HTTP/API Monitoring

**Python requests example:**
```python
import requests

urls = ["https://api.github.com", "https://example.com"]
for url in urls:
    try:
        r = requests.get(url, timeout=5)
        if r.status_code == 200:
            print(f"{url} is up")
        else:
            print(f"{url} returned {r.status_code}")
    except requests.exceptions.RequestException:
        print(f"{url} is down or unreachable")

```

## 🔹 Traceroute & Route

**Trace path to host (Bash):**
```
traceroute google.com
```
Show routing table (Bash):
```
ip route show
```
Python example (check route with ICMP):
```python
from scapy.all import *

res = sr1(IP(dst="8.8.8.8")/ICMP(), timeout=2)
if res:
    print("Next hop:", res.src)
```
## 🔹 Network Scanning

**Discover open ports with nmap:**
```
nmap -p 22,80,443 192.168.1.0/24
```
Scan hosts in subnet:
```
nmap -sn 192.168.1.0/24
```

## 🔹 Combining Bash & Python for DevOps

- Automate host monitoring with Bash scripts
    
- Use Python to analyze network data, API responses, or logs
    
- Schedule scripts with **cron** or **systemd timers**
    

---

> [!tip]  
> Practice combining **network theory + Bash + Python**:

- Ping hosts and log results
    
- Check ports and services
    
- Monitor APIs
    
- Automate alerts for unreachable hosts  
    This is the **core of DevOps network automation**.