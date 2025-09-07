# 🖧 IP Addressing & Subnetting (DevOps)

[[Protocols]] ← Previous | Next → [[Routing]]

> [!info] Purpose
IP addressing and subnetting are essential for **network configuration, monitoring, and automation**.  
DevOps engineers must understand **IP types, subnet masks, and CIDR** to work with servers and cloud networks.

---

## 🔹 IP Address Basics
- **IPv4**: 32-bit addresses, e.g., `192.168.1.10`  
- **IPv6**: 128-bit addresses, e.g., `2001:0db8::1`  
- IPv4 divided into **Network** and **Host** parts using a **subnet mask**  

**Example subnet mask:**
IP: 192.168.1.10  
Subnet: 255.255.255.0  
Network: 192.168.1.0  
Host range: 192.168.1.1 – 192.168.1.254


---

## 🔹 Public vs Private IPs
- **Public IPs** → globally reachable (Internet)  
- **Private IPs** → internal networks  
  - IPv4 private ranges:  
    - 10.0.0.0 – 10.255.255.255  
    - 172.16.0.0 – 172.31.255.255  
    - 192.168.0.0 – 192.168.255.255  

---

## 🔹 CIDR Notation
- CIDR = Classless Inter-Domain Routing  
- Format: `192.168.1.0/24` → 24 bits for network  
- Calculates **number of hosts**: `2^(32-mask) - 2`  

**Example:**
192.168.1.0/24 → 256 addresses → 254 usable hosts

---

## 🔹 Subnetting Example
- Network: `192.168.1.0/24`  
- Split into 4 subnets → /26  

Subnet1: 192.168.1.0/26 Hosts: 62  
Subnet2: 192.168.1.64/26 Hosts: 62  
Subnet3: 192.168.1.128/26 Hosts: 62  
Subnet4: 192.168.1.192/26 Hosts: 62


- Helps organize **servers, VLANs, and services**  

---

## 🔹 Tools for DevOps
- **Bash**: `ip addr`, `ifconfig`, `ping`, `netstat`  
- **Python**: `ipaddress` module  

**Python example:**
```python
import ipaddress

net = ipaddress.ip_network("192.168.1.0/24")
for ip in net.hosts():
    print(ip)

```

## Best Practices

- Always plan **network ranges** for servers and containers
    
- Use **private IPs** internally and NAT for external access
    
- Document **subnets and host allocation** in DevOps environment
    

---

> [!tip]  
> Understanding IPs and subnetting is crucial for:

- Configuring servers and firewalls
    
- Automating deployment scripts
    
- Monitoring network resources efficiently