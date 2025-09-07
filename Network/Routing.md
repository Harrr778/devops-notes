# 🛣 Routing & NAT (DevOps)

[[IP & Subnet]] ← Previous | Next → [[Security]]

> [!info] Purpose
Routing determines **how packets travel across networks**.  
DevOps engineers must understand **default gateways, NAT, and DHCP** to manage servers, cloud networks, and automation scripts.

---

## 🔹 What is Routing?
- Routing is the process of **forwarding packets** from source to destination  
- Performed by **routers** or layer 3 devices  
- Types:  
  - **Static routing** → manually configur
## 🔹 NAT (Network Address Translation)

- Translates **private IPs to public IPs** for Internet access
    
- Types:
    
    - **Static NAT** → fixed translation
        
    - **Dynamic NAT** → pool of IPs
        
    - **PAT (Port Address Translation)** → many-to-one mapping
        

**Example (Linux iptables PAT):**

```bash
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

```

## DHCP (Dynamic Host Configuration Protocol)

- Automatically assigns **IP addresses, subnet masks, gateways** to hosts
    
- Essential for DevOps when provisioning servers or containers
    
- Tools: `dhclient`, `systemctl status dhcpd`
    

---

## 🔹 Routing Table Example
```bash
$ ip route
default via 192.168.1.1 dev eth0
192.168.1.0/24 dev eth0 proto kernel scope link src 192.168.1.100
10.0.0.0/8 via 192.168.1.1 dev eth0

```
Shows network destinations and next hops

## 🔹 Tools for DevOps

- **Bash**: `ip route`, `traceroute`, `ping`, `netstat`, `ss`
    
- **Python**: `scapy` for packet analysis and testing routing
    

**Python example (check route):**

```bash
from scapy.all import *

res = sr1(IP(dst="8.8.8.8")/ICMP(), timeout=2)
if res:
    print(res.src)

```

## 🔹 Best Practices

- Document **network topology** in your DevOps environment
    
- Use **static routes** for critical infrastructure
    
- Combine **NAT + DHCP + routing automation** for cloud servers and containers
    

---

> [!tip]  
> Understanding routing is essential for:

- Ensuring server connectivity
    
- Troubleshooting network issues
    
- Automating deployments that span multiple networks