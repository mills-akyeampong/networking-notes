# Subnetting:

## Table of Contents
- [Subnetting:](#subnetting)
  - [Table of Contents](#table-of-contents)
  - [Basics of IP Addresses](#basics-of-ip-addresses)
  - [Why Subnetting is Needed](#why-subnetting-is-needed)
  - [Key Concepts in Subnetting](#key-concepts-in-subnetting)
  - [Step-by-Step Subnetting Example](#step-by-step-subnetting-example)
    - [Step 1: Determine the Largest Subnet Needed](#step-1-determine-the-largest-subnet-needed)
    - [Step 2: Calculate Subnet Masks](#step-2-calculate-subnet-masks)
    - [Step 3: Allocate Subnets](#step-3-allocate-subnets)
    - [Step 4: Summary Table](#step-4-summary-table)
  - [Real-World Tips](#real-world-tips)
  - [Quick Reference](#quick-reference)
  - [Conclusion](#conclusion)

---

## Basics of IP Addresses

An IP address is like a home address for devices on a network. It has **two main parts**:

1. **Network ID** – Identifies the network (like the street name).  
2. **Host ID** – Identifies the device (like the house number).  

IP addresses are written in **IPv4** format:

```

192.168.0.1

```

- **192.168.0** → Network part  
- **1** → Host part  

A **subnet mask** defines which part is network and which part is host:

- Example: `255.255.255.0`  
  - `255.255.255` → Network  
  - `0` → Host  

This means the last 8 bits are for devices (hosts) in that network.

---

## Why Subnetting is Needed

Imagine a company with **192.168.0.0/24 network**, which can host **256 devices**.  
But the company has **3 departments**:

- HR: 50 devices  
- IT: 100 devices  
- Sales: 70 devices  

Instead of using all IPs in one network, we **divide it** to avoid IP wastage and improve security.

---

## Key Concepts in Subnetting

- **CIDR Notation**: `/24` means 24 bits are network bits.  
- **Subnet mask**: Indicates network vs host bits.  
- **Number of subnets**: `2^n` (where n = number of bits borrowed from host).  
- **Number of hosts per subnet**: `2^h - 2` (where h = number of host bits; subtract 2 for network & broadcast addresses).  

---

## Step-by-Step Subnetting Example

**Problem:**  
IP Range: `192.168.0.0 – 192.168.0.255`  
Divide for **3 departments**: HR (50), IT (100), Sales (70)

---

### Step 1: Determine the Largest Subnet Needed

- IT needs 100 devices → nearest power of 2 = 128 (2^7)  
- Check: `2^7 - 2 = 126 hosts` → Enough for IT ✅

- Sales: 70 devices → next power of 2 = 128 → /25 ✅  
- HR: 50 devices → next power of 2 = 64 → /26 ✅

---

### Step 2: Calculate Subnet Masks

- `/25` → 255.255.255.128 → 128 addresses per subnet  
- `/26` → 255.255.255.192 → 64 addresses per subnet  

---

### Step 3: Allocate Subnets

Original network: `192.168.0.0/24`  

1. **IT** (largest first): /25 → 192.168.0.0 – 192.168.0.127  
   - Network: 192.168.0.0  
   - Broadcast: 192.168.0.127  
   - Usable hosts: 192.168.0.1 – 192.168.0.126  

2. **Sales**: /26 → 192.168.0.128 – 192.168.0.191  
   - Network: 192.168.0.128  
   - Broadcast: 192.168.0.191  
   - Usable hosts: 192.168.0.129 – 192.168.0.190  

3. **HR**: /26 → 192.168.0.192 – 192.168.0.255  
   - Network: 192.168.0.192  
   - Broadcast: 192.168.0.255  
   - Usable hosts: 192.168.0.193 – 192.168.0.254  

---

### Step 4: Summary Table

| Department | Subnet Address     | Broadcast Address  | Usable IPs           | Subnet Mask      |
|------------|------------------|-----------------|--------------------|----------------|
| IT         | 192.168.0.0       | 192.168.0.127   | 192.168.0.1-126    | 255.255.255.128 (/25) |
| Sales      | 192.168.0.128     | 192.168.0.191   | 192.168.0.129-190  | 255.255.255.192 (/26) |
| HR         | 192.168.0.192     | 192.168.0.255   | 192.168.0.193-254  | 255.255.255.192 (/26) |

---

## Real-World Tips

1. Always **start with the largest subnet first**.  
2. Remember to **reserve network & broadcast addresses**.  
3. Use **powers of 2** for host numbers.  
4. Document your subnets clearly for easy management.  

---

## Quick Reference

| Subnet Bits | Hosts per Subnet |
|------------|----------------|
| /30        | 2              |
| /29        | 6              |
| /28        | 14             |
| /27        | 30             |
| /26        | 62             |
| /25        | 126            |
| /24        | 254            |

---

## Conclusion

Subnetting might seem tricky, but if you:

1. Identify the number of hosts needed  
2. Use powers of 2  
3. Assign largest subnets first  

…it becomes simple and logical. Subnetting is just smartly **splitting your network** to avoid wasting IPs.