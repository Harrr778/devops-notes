# 🌐 History of the Internet

Next → [[Layers]]

> [!info] Purpose
Learn how networking evolved from early experiments to the modern Internet.  
This knowledge helps DevOps engineers **understand protocols, troubleshoot networks, and automate tasks**.

---

## 🔹 Early Networks (1960s–1970s)
- **ARPANET (1969)** – first packet-switching network, funded by DARPA  
  - Connected 4 research computers  
  - Introduced **packet switching** instead of dedicated circuits  
- **NCP (Network Control Protocol)** – predecessor of TCP/IP  
- **Ethernet (1973)** – local area networking standard, developed by Xerox PARC  

---

## 🔹 Birth of TCP/IP (1970s–1980s)
- **TCP (Transmission Control Protocol)** and **IP (Internet Protocol)** developed by Vint Cerf & Bob Kahn  
- **1978:** First demonstration of TCP/IP between 2 networks  
- **1983:** TCP/IP becomes standard for ARPANET → foundation of the modern Internet  

---

## 🔹 Expansion to Universities and Commercial Networks
- 1980s: NSFNET connects US universities, expanding the network  
- 1989–1990: Tim Berners-Lee creates the **World Wide Web**  
  - HTML, HTTP, and URLs  
- 1991: Public access to the Internet grows rapidly  

---

## 🔹 Key Protocols Introduced Early On
- **ICMP** – for network diagnostics (ping)  
- **FTP** – file transfer protocol  
- **SMTP** – email transfer protocol  
- **Telnet / SSH** – remote login and management  

---

## 🔹 Internet in the 1990s–2000s
- Commercial ISPs emerge  
- DNS (Domain Name System) standardizes addresses  
- HTTP and browsers make the Internet accessible to everyone  

---

## 🔹 Why History Matters for DevOps
- Most DevOps automation **relies on TCP/IP networking**  
- Knowing history helps:
  - Understand **why protocols work the way they do**  
  - Troubleshoot network problems efficiently  
  - Automate monitoring, deployment, and configuration tasks  

---

> [!tip]
DevOps engineers should know which **layer each tool or protocol works at**:  
- `ping` → ICMP, Network layer  
- `ssh` → TCP, Transport layer  
- `http/https` → Application layer