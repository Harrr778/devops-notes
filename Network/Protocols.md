# 📡 Network Protocols (DevOps)

[[Layers]] ← Previous | Next → [[IP & Subnet]]

> [!info] Purpose
Protocols define **how devices communicate** over a network.  
DevOps engineers must understand protocols to automate, monitor, and troubleshoot networks.

---

## 🔹 TCP (Transmission Control Protocol)
- Connection-oriented, reliable  
- Guarantees data delivery, order, and error checking  
- Common uses: SSH, HTTP, HTTPS, FTP  
- Tools: `netcat`, `curl`, `telnet`  

**Example (Python socket):**
```python
import socket

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.connect(("example.com", 80))
```

## 🔹 UDP (User Datagram Protocol)

- Connectionless, faster, no guaranteed delivery
    
- Common uses: DNS queries, video streaming, DHCP
    
- Tools: `netcat -u`, `iperf`

Example (Python UDP):
```python
import socket
sock = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
sock.sendto(b"hello", ("example.com", 53))
```

## 🔹 HTTP / HTTPS

- Application layer protocols for web communication
    
- HTTP → plain text, HTTPS → encrypted (TLS/SSL)
    
- Tools: `curl`, `httpie`, Python `requests`

Example (Python requests):
```python
import requests
r = requests.get("https://api.github.com")
print(r.status_code)
```

## 🔹 DNS (Domain Name System)

- Resolves domain names to IP addresses
    
- Uses UDP (query) and TCP (zone transfers)
    
- Tools: `dig`, `nslookup`, Python `dnspython`
    

---

## 🔹 ICMP (Internet Control Message Protocol)

- Used for network diagnostics: `ping`, `traceroute`
    
- No data payload, only control messages
    
- Example tool: `ping google.com`
    

---

## 🔹 SSH (Secure Shell)

- Secure remote login, encrypted transport over TCP
    
- Common DevOps use: remote server management, automated scripts
    
- Tools: `ssh`, `scp`, `paramiko` (Python)
    

---

## 🔹 Other Important Protocols

- **FTP/SFTP** → file transfer
    
- **SMTP/IMAP/POP3** → email
    
- **ARP** → maps IP to MAC addresses on LAN
    

---

> [!tip]  
> DevOps scripts often interact with **TCP/UDP/HTTP/DNS/SSH**.

- For monitoring → ICMP, TCP port check
    
- For automation → SSH, HTTP API
    
- For file transfer → SFTP/FTP