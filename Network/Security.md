# 🛡 Network Security (DevOps)

[[Routing]] ← Previous | Next → [[Network/Practice]]

> [!info] Purpose
Network security is essential for **protecting servers, services, and data**.  
DevOps engineers must understand **firewalls, encryption, VPNs, and common attacks** to automate secure deployments.

---

## 🔹 Firewalls
- Control traffic between networks based on rules  
- Types:  
  - **Host-based** → `ufw`, `firewalld`, `iptables`  
  - **Network-based** → routers, cloud security groups  

**Bash example (allow SSH & HTTP using ufw):**
```bash
sudo ufw allow 22/tcp
sudo ufw allow 80/tcp
sudo ufw enable
```

## 🔹 TLS / SSL

- Encrypts communication between client and server
    
- Used in HTTPS, API requests, email (SMTP/IMAP)
    
- Tools: `openssl`, Python `ssl`, `requests` with verify
    

**Python example (HTTPS request):**

```python 
import requests

r = requests.get("https://api.github.com", verify=True)
print(r.status_code)

```

---

## 🔹 VPN (Virtual Private Network)

- Creates **secure encrypted tunnels** over public networks
    
- Common uses: remote server access, secure cloud connections
    
- Tools: OpenVPN, WireGuard

## 🔹 Common Network Attacks

|Attack Type|Description|DevOps Consideration|
|---|---|---|
|DDoS|Overload server with requests|Rate limiting, monitoring|
|Man-in-the-Middle|Intercept unencrypted traffic|Use TLS/SSL, VPN|
|Port Scanning|Discover open ports|Firewall, fail2ban|
|ARP Spoofing|Fake MAC/IP to intercept LAN traffic|Use static ARP entries|

---

## 🔹 Security Best Practices for DevOps

- **Use firewalls** to restrict access to servers
    
- **Encrypt traffic** (HTTPS, VPN)
    
- **Monitor logs** for suspicious activity (`fail2ban`, `journalctl`)
    
- **Automate security updates** on servers and containers
    
- **Document security policies** for cloud and internal networks
    

---

## 🔹 Useful Tools for DevOps

- `iptables` / `ufw` / `firewalld` → firewall configuration
    
- `openssl` → check certificates and encrypt data
    
- `tcpdump` / `wireshark` → capture and analyze packets
    
- `nmap` → discover hosts and open ports
    

---

> [!tip]  
> Network security is **not optional for DevOps**.  
> Always combine: **firewall + encryption + monitoring + automation** to keep servers and services safe.