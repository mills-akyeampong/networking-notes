# IP Address

## 1. Introduction

An **IP Address (Internet Protocol Address)** is a unique number assigned to each device connected to a network. It serves **two main purposes**:

1. **Identification** → Identifies a device (computer, phone, router, etc.).
2. **Location addressing** → Provides the device’s location on the network.

👉 Think of an IP address like a **house address**: it tells the network *who* you are and *where* to deliver data.

---

## 2. Why IP Addresses Are Important

Without IP addresses, devices on a network wouldn’t know **who is sending** or **where data should go**.

Example: When you type **[www.google.com](http://www.google.com)**:

1. DNS converts the name into an IP address.
2. Your browser sends a request to that IP.
3. Google’s server responds → the page loads.

---

## 3. Versions of IP Address

### 3.1 IPv4 (Internet Protocol version 4)

* **32-bit address** → ~4.3 billion unique addresses.
* Written as four numbers separated by dots: `192.168.1.1`.
* Each number ranges **0–255**.
* Most common today.

⚠️ Limitation: Internet grew too fast, and IPv4 addresses are running out.

---

### 3.2 IPv6 (Internet Protocol version 6)

* **128-bit address** → ~340 undecillion addresses (virtually unlimited).
* Written in hexadecimal, separated by colons: `2001:db8::1`.
* Advantages:
  * Built-in **security (IPSec)**.
  * **Auto-configuration** support.
  * No need for NAT (Network Address Translation).

---

## 4. Structure of IP Address

### 4.1 IPv4

* Divided into **4 octets** (8 bits each).
* Example: `192.168.0.1` → `11000000.10101000.00000000.00000001` in binary.

### 4.2 IPv6

* Divided into **8 groups of 16-bit hexadecimal numbers**.
* Example: `2001:0db8:0000:0000:0000:ff00:0042:8329`.
* Shortened: `2001:db8::ff00:42:8329`.

---

## 5. Types of IP Addresses

### 5.1 Based on Function

* **Private IP** → used inside LAN (not routable on internet).
  * Ranges:
    * `10.0.0.0 – 10.255.255.255`
    * `172.16.0.0 – 172.31.255.255`
    * `192.168.0.0 – 192.168.255.255`
* **Public IP** → unique address used on the internet, assigned by ISP.

---

### 5.2 Based on Permanency

* **Static IP** → Manually set, does not change. Useful for servers & hosting.
* **Dynamic IP** → Automatically assigned by **DHCP**, changes over time. Common for home users.

---

### 5.3 Based on Communication

* **Unicast** → One-to-one communication.
* **Broadcast** → One-to-all communication (IPv4 only).
* **Multicast** → One-to-many (selected group).
* **Anycast** → One-to-nearest (common in IPv6).

---

## 6. Classes of IPv4 Address

| Class | First Octet Range | Full IP Address Range              | Default Subnet Mask | Usage                 |
|-------|------------------|------------------------------------|---------------------|-----------------------|
| A     | 1 – 126          | 1.0.0.0 – 126.255.255.255          | 255.0.0.0 (/8)      | Very large networks   |
| B     | 128 – 191        | 128.0.0.0 – 191.255.255.255        | 255.255.0.0 (/16)   | Medium networks       |
| C     | 192 – 223        | 192.0.0.0 – 223.255.255.255        | 255.255.255.0 (/24) | Small networks        |
| D     | 224 – 239        | 224.0.0.0 – 239.255.255.255        | N/A                 | Multicast             |
| E     | 240 – 255        | 240.0.0.0 – 255.255.255.255        | N/A                 | Research/Experimental |

⚠️ Notes:
- `127.0.0.0 – 127.255.255.255` → Reserved for **loopback (localhost)**.
- `0.0.0.0` → Used as a default route (unspecified address).


---

## 7. Special IP Addresses

* **127.0.0.1** → Loopback (your own machine).
* **0.0.0.0** → Default route or “any address.”
* **255.255.255.255** → Broadcast to all devices.
* **169.254.x.x** → APIPA (assigned when DHCP fails).

---

## 8. Subnetting

**Subnetting** = dividing a large network into smaller ones.

Benefits:

* Efficient IP use.
* Improved network performance.
* Better security.

Example:

* Network: `192.168.1.0/24` (254 usable hosts).
* Subdivide into:
  * `192.168.1.0/26`
  * `192.168.1.64/26`
  * `192.168.1.128/26`
  * `192.168.1.192/26`

Each subnet can serve a department in a company.

---

## 9. IPv4 vs IPv6 Comparison

| Feature         | IPv4                  | IPv6                                   |
| --------------- | -------------------- | ------------------------------------- |
| Size            | 32-bit               | 128-bit                               |
| Notation        | Decimal (192.168.1.1)| Hexadecimal (2001:db8::1)             |
| Total addresses | ~4.3 billion         | ~340 undecillion                       |
| Security        | Optional (IPSec)     | Built-in IPSec                         |
| Broadcast       | Supported            | Not supported (uses multicast/anycast)|
| Configuration   | Manual/DHCP          | Auto-configuration supported           |

---

## 10. Real-World Applications

* **Hosting websites** → requires static public IP.
* **Home Wi-Fi** → devices use private IPs, router uses NAT + public IP.
* **VPNs & Remote Work** → rely on IPs for tunneling.
* **Online Gaming** → depends on unique IPs for connectivity.
* **Security** → Firewalls use IPs to allow/deny access.

---

## 11. Frequently Asked Questions (FAQ)

**Q1: Can two devices have the same IP?**

* On same network: ❌ No, it causes conflict.
* On different networks: ✅ Yes (private IPs can repeat).

**Q2: Why do I see 192.168.x.x on my laptop/phone instead of my real IP?**

* That’s your **private IP** from the router.
* Your **ISP assigns the router a public IP**.

**Q3: Why do we need IPv6 if IPv4 is still working?**

* IPv4 addresses are almost exhausted.
* IPv6 supports unlimited addresses and advanced features.

**Q4: What is “localhost”?**

* It refers to your own computer, usually `127.0.0.1`.

---

## 12. Summary

* IP Address = **unique identifier** for devices on a network.
* Two versions: **IPv4 (32-bit)** and **IPv6 (128-bit)**.
* Types: **Private/Public, Static/Dynamic**.
* IPv4 has **classes** and **special addresses**.
* **Subnetting** divides networks for efficiency.
* Every time you use the internet, IP addresses make the communication possible.

👉 **In simple terms:** An IP address is the **digital address of a device**, ensuring data knows *who* to reach and *where* to go.