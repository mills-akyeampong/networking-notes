# IP Address

> **Author**: Mills Kojo Akyeampong  
> **Role**: Security Systems & Network Engineer    
> **Intended Audience**: Networking students, professionals, self-learners

---

## 📚 Table of Contents

- [IP Address](#ip-address)
  - [📚 Table of Contents](#-table-of-contents)
  - [1. Introduction](#1-introduction)
  - [2. Why IP Addresses Are Important](#2-why-ip-addresses-are-important)
  - [3. Versions of IP Address](#3-versions-of-ip-address)
    - [3.1 IPv4 (Internet Protocol version 4)](#31-ipv4-internet-protocol-version-4)
    - [3.2 IPv6 (Internet Protocol version 6)](#32-ipv6-internet-protocol-version-6)
  - [4. Structure of IP Address](#4-structure-of-ip-address)
    - [4.1 IPv4](#41-ipv4)
    - [4.2 IPv6](#42-ipv6)
  - [5. Types of IP Addresses](#5-types-of-ip-addresses)
    - [5.1 Based on Function](#51-based-on-function)
    - [5.2 Based on Permanency](#52-based-on-permanency)
    - [5.3 Based on Communication](#53-based-on-communication)
  - [6. Classes of IPv4 Address](#6-classes-of-ipv4-address)
  - [7. Special IP Addresses](#7-special-ip-addresses)
  - [8. Subnetting](#8-subnetting)
    - [Benefits:](#benefits)
    - [Example:](#example)
  - [9. IPv4 vs IPv6 Comparison](#9-ipv4-vs-ipv6-comparison)
  - [10. Real-World Applications](#10-real-world-applications)
  - [11. Frequently Asked Questions (FAQ)](#11-frequently-asked-questions-faq)

---

## 1. Introduction

An **IP Address (Internet Protocol Address)** is a unique identifier assigned to each device on a network. It serves two key purposes:

1. **Identification** – Who the device is  
2. **Location addressing** – Where the device is in the network  

> Think of an IP address like a house address: it tells the network *who* you are and *where* to send data.

---

## 2. Why IP Addresses Are Important

Without IP addresses, devices wouldn’t know:

- Who is sending the data  
- Where the data should go  

**Example**:  
Typing `www.google.com` in a browser:

1. DNS translates the domain to an IP address  
2. Your device sends a request to that IP  
3. The server responds with the web page  

---

## 3. Versions of IP Address

### 3.1 IPv4 (Internet Protocol version 4)

- **32-bit address**  
- Written in dotted-decimal format (e.g., `192.168.1.1`)  
- Ranges from `0.0.0.0` to `255.255.255.255`  
- ~4.3 billion unique addresses  

⚠️ Limitation: IPv4 is running out due to internet growth.

---

### 3.2 IPv6 (Internet Protocol version 6)

- **128-bit address**  
- Written in hexadecimal (e.g., `2001:db8::1`)  
- Supports ~340 undecillion addresses  
- Supports features like:
  - Built-in **IPSec**
  - **Auto-configuration**
  - No NAT required  

---

## 4. Structure of IP Address

### 4.1 IPv4

- Divided into **4 octets** (8 bits each)  
- Example:  
  `192.168.0.1` → `11000000.10101000.00000000.00000001` (binary)

---

### 4.2 IPv6

- 8 groups of 4 hexadecimal digits  
- Example:  
  Full: `2001:0db8:0000:0000:0000:ff00:0042:8329`  
  Shortened: `2001:db8::ff00:42:8329`

---

## 5. Types of IP Addresses

### 5.1 Based on Function

- **Private IP** – Used in LANs, not routable on the internet  
  - `10.0.0.0 – 10.255.255.255`  
  - `172.16.0.0 – 172.31.255.255`  
  - `192.168.0.0 – 192.168.255.255`  
- **Public IP** – Globally unique, routable on the internet, assigned by ISPs

---

### 5.2 Based on Permanency

- **Static IP** – Manually set, does not change (e.g., servers)  
- **Dynamic IP** – Assigned via DHCP, may change over time

---

### 5.3 Based on Communication

- **Unicast** – One-to-one  
- **Broadcast** – One-to-all (IPv4 only)  
- **Multicast** – One-to-many (group)  
- **Anycast** – One-to-nearest (IPv6 only)

---

## 6. Classes of IPv4 Address

```

| Class | First Octet Range | IP Address Range            | Default Subnet Mask | Usage           |
| ----- | ----------------- | --------------------------- | ------------------- | --------------- |
| A     | 1 – 126           | 1.0.0.0 – 126.255.255.255   | 255.0.0.0 (/8)      | Large networks  |
| B     | 128 – 191         | 128.0.0.0 – 191.255.255.255 | 255.255.0.0 (/16)   | Medium networks |
| C     | 192 – 223         | 192.0.0.0 – 223.255.255.255 | 255.255.255.0 (/24) | Small networks  |
| D     | 224 – 239         | 224.0.0.0 – 239.255.255.255 | N/A                 | Multicast       |
| E     | 240 – 255         | 240.0.0.0 – 255.255.255.255 | N/A                 | Experimental    |

```

> 🔁 `127.0.0.0/8` – Loopback (localhost)  
> 🛑 `0.0.0.0` – Unspecified/default route

---

## 7. Special IP Addresses

- `127.0.0.1` → Loopback (your own machine)  
- `0.0.0.0` → Default route / unspecified address  
- `255.255.255.255` → Broadcast to all on LAN  
- `169.254.x.x` → APIPA (Automatic Private IP Assignment) when DHCP fails

---

## 8. Subnetting

**Subnetting** = dividing a large network into smaller sub-networks (subnets)

### Benefits:

- Efficient use of IPs  
- Improved performance  
- Increased security  

### Example:

Given `192.168.1.0/24` (254 hosts), it can be split into:

- `192.168.1.0/26`  
- `192.168.1.64/26`  
- `192.168.1.128/26`  
- `192.168.1.192/26`

Each subnet can serve a separate department.

---

## 9. IPv4 vs IPv6 Comparison

```

| Feature         | IPv4             | IPv6                           |
| --------------- | ---------------- | ------------------------------ |
| Address Size    | 32-bit           | 128-bit                        |
| Format          | Dotted Decimal   | Hexadecimal with colons        |
| Total Addresses | \~4.3 billion    | \~340 undecillion              |
| Security        | Optional (IPSec) | Built-in (IPSec)               |
| NAT             | Commonly used    | Not needed                     |
| Broadcast       | Supported        | Not supported (uses multicast) |
| Configuration   | Manual/DHCP      | Supports auto-configuration    |

```

---

## 10. Real-World Applications

- **Web Hosting** – Public static IPs for domains  
- **Home Networking** – Private IPs managed by router (NAT)  
- **VPN and Remote Access** – Secure IP tunneling  
- **Gaming** – Public IPs for matchmaking and peer-to-peer  
- **Firewall Rules** – IP-based access control

---

## 11. Frequently Asked Questions (FAQ)

**Q1: Can two devices have the same IP?**  
- On same network: ❌ No (causes conflict)  
- On different networks: ✅ Yes (if using private IPs)

**Q2: Why do I see 192.168.x.x on my device?**  
- That's a **private IP** assigned by your router.

**Q3: Why do we need IPv6?**  
- IPv4 is running out.
```
