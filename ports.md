# Network Ports

> **Author**: Mills Kojo Akyeampong  
> **Role**: Security Systems & Network Engineer    
> **Intended Audience**: Networking students, professionals, self-learners

---

## 📚 Table of Contents

- [Network Ports](#network-ports)
  - [📚 Table of Contents](#-table-of-contents)
  - [📖 Introduction](#-introduction)
  - [🔌 What Is a Port?](#-what-is-a-port)
  - [🗂️ Types of Ports](#️-types-of-ports)
    - [1. Well-Known Ports (0–1023)](#1-well-known-ports-01023)
    - [2. Registered Ports (1024–49151)](#2-registered-ports-102449151)
    - [3. Dynamic/Private Ports (49152–65535)](#3-dynamicprivate-ports-4915265535)
  - [📦 Common TCP \& UDP Ports](#-common-tcp--udp-ports)
  - [⚔️ TCP vs UDP Ports](#️-tcp-vs-udp-ports)
  - [🧩 How Ports Work in Networking](#-how-ports-work-in-networking)
  - [🔒 Security Considerations](#-security-considerations)
  - [🧪 Port Scanning](#-port-scanning)
  - [❓ FAQs](#-faqs)
    - [Q1: Can two services run on the same port?](#q1-can-two-services-run-on-the-same-port)
    - [Q2: What port does a web browser use?](#q2-what-port-does-a-web-browser-use)
    - [Q3: Can a port number be reused?](#q3-can-a-port-number-be-reused)
    - [Q4: How many total ports exist?](#q4-how-many-total-ports-exist)
  - [✅ Conclusion](#-conclusion)

---

## 📖 Introduction

In networking, a **port** is a **virtual point** where network connections start and end.  
Ports allow multiple services or applications to run on a single device using a single IP address.

---

## 🔌 What Is a Port?

A **port** is a **16-bit number** (range: 0 to 65535) used to **identify specific processes or services** on a networked device.

- IP address = *who to talk to*  
- Port number = *what service to talk to*

📍 **Example**:  
When accessing a website:  
- IP: `172.217.10.14` (Google)  
- Port: `80` (HTTP)

---

## 🗂️ Types of Ports

### 1. Well-Known Ports (0–1023)

- Assigned by **IANA (Internet Assigned Numbers Authority)**
- Used by core services (HTTP, FTP, DNS, etc.)
- Require **admin privileges** to bind

### 2. Registered Ports (1024–49151)

- Used by **software applications** (e.g., databases, games)
- Less strictly regulated
- Can be registered with IANA

### 3. Dynamic/Private Ports (49152–65535)

- **Ephemeral ports**: temporarily assigned by the OS
- Used for **client-side connections**
- Not registered or reserved

---

## 📦 Common TCP & UDP Ports

| Port | Protocol | Service                | Description                     |
|------|----------|------------------------|---------------------------------|
| 20   | TCP      | FTP (Data)             | File transfer (data stream)     |
| 21   | TCP      | FTP (Control)          | File Transfer Protocol (login)  |
| 22   | TCP      | SSH                    | Secure Shell remote access      |
| 23   | TCP      | Telnet                 | Unencrypted remote login        |
| 25   | TCP      | SMTP                   | Outgoing email                  |
| 53   | UDP/TCP  | DNS                    | Domain name resolution          |
| 67   | UDP      | DHCP (Server)          | Dynamic IP address assignment   |
| 68   | UDP      | DHCP (Client)          | Receives IP configuration       |
| 69   | UDP      | TFTP                   | Trivial FTP (no authentication) |
| 80   | TCP      | HTTP                   | Web traffic                     |
| 110  | TCP      | POP3                   | Incoming email                  |
| 123  | UDP      | NTP                    | Network time synchronization    |
| 143  | TCP      | IMAP                   | Email retrieval                 |
| 161  | UDP      | SNMP                   | Network management              |
| 194  | TCP      | IRC                    | Internet Relay Chat             |
| 443  | TCP      | HTTPS                  | Secure web traffic              |
| 445  | TCP      | SMB                    | Windows file sharing            |
| 514  | UDP      | Syslog                 | Logging system events           |
| 587  | TCP      | SMTP (Secure)          | Outgoing email (secure)         |
| 993  | TCP      | IMAPS                  | Secure IMAP                     |
| 995  | TCP      | POP3S                  | Secure POP3                     |
| 3306 | TCP      | MySQL                  | Database server                 |
| 3389 | TCP      | RDP                    | Remote Desktop Protocol         |
| 5060 | UDP/TCP  | SIP                    | VoIP signaling                  |
| 8080 | TCP      | HTTP (Alt)             | Alternate HTTP port             |

---

## ⚔️ TCP vs UDP Ports

| Feature           | TCP                         | UDP                        |
|------------------|-----------------------------|----------------------------|
| Connection        | Connection-oriented         | Connectionless             |
| Reliability       | Reliable (error-checked)    | Unreliable (no guarantee)  |
| Speed             | Slower                      | Faster                     |
| Use Cases         | Web, email, file transfer   | Streaming, DNS, VoIP       |
| Example Ports     | 80 (HTTP), 443 (HTTPS)      | 53 (DNS), 69 (TFTP)        |

---

## 🧩 How Ports Work in Networking

When a device communicates over a network:
- It uses an **IP address** to identify the target host
- It uses a **port number** to identify the service on that host

🖥️ Example:  
Your browser →  
- Destination IP: `216.58.223.206`  
- Destination Port: `443` (HTTPS)

The receiving web server listens on port `443` and responds accordingly.

---

## 🔒 Security Considerations

- **Open ports** can be exploited by attackers.
- Unused ports should be **closed or filtered** via firewall.
- Use **port security and firewalls** to control traffic.
- Tools like `iptables`, `ufw`, `Windows Firewall`, or enterprise appliances can manage port access.

---

## 🧪 Port Scanning

**Port scanning** is the process of probing a device to discover:
- Which ports are open
- What services are running
- If there are vulnerabilities

🛠️ Tools:
- `Nmap`
- `Netcat`
- `Zenmap` (GUI version of Nmap)

⚠️ **Note**: Unauthorized port scanning can be considered illegal or malicious.

---

## ❓ FAQs

### Q1: Can two services run on the same port?
- ❌ No, unless they're on **different IP addresses** or **virtual interfaces**.

### Q2: What port does a web browser use?
- Typically **port 80 (HTTP)** or **port 443 (HTTPS)**.

### Q3: Can a port number be reused?
- ✅ Yes, once the previous connection using it has been closed and released.

### Q4: How many total ports exist?
- **65,536** (0–65535). Port numbers are 16-bit unsigned integers.

---

## ✅ Conclusion

Ports are essential for network communication, enabling multiple services to operate on a single device.  
Understanding ports allows you to:
- Configure firewalls properly
- Troubleshoot network issues
- Secure services against unwanted access

🎯 **In summary:**  
> Ports = Service Identifiers  
> IP = Device Identifier  
Together, they form the foundation of all network communication.