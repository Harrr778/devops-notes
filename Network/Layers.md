# 🏗 Network Layers (OSI & TCP/IP)

[[History]] ← Previous | Next → [[Protocols]]

> [!info] Purpose
Understanding network layers is essential for **DevOps automation, monitoring, and troubleshooting**.  
Each layer has its **protocols, tools, and responsibilities**.

---

## 🔹 OSI Model (7 Layers)
| Layer | Name                | Function & Example Tools                     |
|-------|-------------------|--------------------------------------------|
| 7     | Application        | HTTP, HTTPS, FTP, SMTP, DNS                |
| 6     | Presentation       | Data encryption/decryption, SSL/TLS        |
| 5     | Session            | Establish/terminate sessions, e.g., SSH    |
| 4     | Transport          | TCP (reliable), UDP (fast, connectionless) |
| 3     | Network            | IP addressing, routing, ICMP, ping         |
| 2     | Data Link          | Ethernet, MAC addresses, switch forwarding |
| 1     | Physical           | Cables, Wi-Fi, electrical signals          |

> [!tip]
When automating network tasks:  
- `ping` → Network layer  
- `curl` → Application layer  
- `ssh` → Session/Transport layer  

---

## 🔹 TCP/IP Model (4 Layers)
| Layer        | Maps To OSI Layer | Example Protocols                   |
|-------------|-----------------|-----------------------------------|
| Application | OSI 5–7         | HTTP, FTP, SMTP, DNS, SSH          |
| Transport   | OSI 4           | TCP, UDP                           |
| Internet    | OSI 3           | IP, ICMP, ARP                      |
| Network Access | OSI 1–2       | Ethernet, Wi-Fi                     |

- TCP/IP is **practical model used in real networks**  
- OSI is more **conceptual**, useful for understanding layers  

---

## 🔹 Layer Responsibilities for DevOps
- **Application**: API checks, HTTP requests  
- **Transport**: Reliability vs speed (TCP vs UDP)  
- **Network**: IP routing, network monitoring  
- **Data Link & Physical**: Hardware issues, cabling, NIC status  

---

## 🔹 Common Layer Tools
- **Application**: `curl`, `wget`, `httpie`  
- **Transport**: `netcat`, `nmap`, `iperf`  
- **Network**: `ping`, `traceroute`, `tcpdump`  
- **Data Link/Physical**: `ethtool`, `ifconfig/ip`, Wireshark  

---

> [!tip]
Always identify **which layer your script interacts with** when building DevOps automation.  
Example: a Python script using `socket` → Transport layer, `requests` → Application layer.