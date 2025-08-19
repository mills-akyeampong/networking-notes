# Firewall

## Table of Contents
- [Firewall](#firewall)
  - [Table of Contents](#table-of-contents)
  - [Introduction to Firewalls](#introduction-to-firewalls)
  - [Importance of Firewalls](#importance-of-firewalls)
  - [Firewall Types](#firewall-types)
    - [Network-Based Firewalls](#network-based-firewalls)
    - [Host-Based Firewalls](#host-based-firewalls)
    - [Application Firewalls](#application-firewalls)
    - [Cloud Firewalls](#cloud-firewalls)
  - [Firewall Technologies](#firewall-technologies)
    - [Stateless / Packet Filtering](#stateless--packet-filtering)
    - [Stateful Inspection](#stateful-inspection)
    - [Proxy Firewalls](#proxy-firewalls)
    - [Next-Generation Firewalls (NGFW)](#next-generation-firewalls-ngfw)
  - [Firewall Architectures](#firewall-architectures)
    - [Bastion Host](#bastion-host)
    - [Screened Subnet (DMZ)](#screened-subnet-dmz)
  - [Common Firewall Vendors and Software](#common-firewall-vendors-and-software)
  - [Firewall Configuration Basics](#firewall-configuration-basics)
    - [Rules and Policies](#rules-and-policies)
    - [Zones and Interfaces](#zones-and-interfaces)
    - [Logging and Monitoring](#logging-and-monitoring)
  - [Best Practices](#best-practices)
  - [Summary](#summary)
  - [Example Commands](#example-commands)
    - [Windows Defender Firewall](#windows-defender-firewall)
    - [Linux ufw](#linux-ufw)
    - [Linux iptables](#linux-iptables)
- [Block all incoming traffic except SSH](#block-all-incoming-traffic-except-ssh)
- [Save rules](#save-rules)

---

## Introduction to Firewalls
A **firewall** is a network security device (hardware or software) that monitors, filters, and controls **incoming and outgoing network traffic** based on predetermined security rules.  
It acts as a **barrier** between trusted internal networks and untrusted external networks (like the internet).  

---

## Importance of Firewalls
- Protects devices and networks from unauthorized access.
- Prevents attacks such as malware, ransomware, and hacking attempts.
- Controls traffic flow, allowing only legitimate communications.
- Monitors network activity for suspicious behavior.

---

## Firewall Types

### Network-Based Firewalls
- Placed at the **perimeter of the network**.
- Protect the entire network from external threats.  
**Examples:** Cisco ASA, Fortinet FortiGate, Juniper SRX

### Host-Based Firewalls
- Installed **on individual devices** (hosts).
- Protects that specific host.  
**Examples:** Windows Defender Firewall, macOS Application Firewall, Linux `iptables` / `ufw`

### Application Firewalls
- Monitors and controls traffic at the **application layer (Layer 7)**.
- Can filter based on **application type** or **HTTP requests**.  
**Examples:** ModSecurity, Cloudflare WAF

### Cloud Firewalls
- Deployed in cloud environments.
- Protect virtual networks and cloud workloads.  
**Examples:** AWS WAF, Azure Firewall, Google Cloud Firewall

---

## Firewall Technologies

### Stateless / Packet Filtering
- Examines **individual packets** independently, without keeping track of connection state.
- Makes decisions based on **source IP, destination IP, port, and protocol** only.
- **Pros:** Fast and simple  
- **Cons:** Cannot track sessions, less secure, easy to bypass

### Stateful Inspection
- Tracks **active connections** and session information.
- Allows only packets that are part of a **valid, established connection**.
- More secure than stateless firewalls.

### Proxy Firewalls
- Acts as an **intermediary** between internal users and the internet.
- Can filter content and hide internal IPs.
- **Pros:** Inspects application layer traffic  
- **Cons:** Can slow down performance

### Next-Generation Firewalls (NGFW)
- Combines traditional firewall with **deep packet inspection, intrusion prevention, and application awareness**.
- Often includes **VPN support, antivirus scanning, and URL filtering**.

---

## Firewall Architectures

### Bastion Host
- Dedicated, hardened server exposed to the internet.
- Hosts firewall software or acts as a gateway.

### Screened Subnet (DMZ)
- A **demilitarized zone** separates internal network from public-facing services.
- Hosts public servers (web, email) with controlled access.

---

## Common Firewall Vendors and Software
| Vendor / Software | Type | Key Features | Platform |
|------------------|------|--------------|----------|
| Cisco ASA | Network | VPN, Stateful Inspection | Hardware |
| Fortinet FortiGate | Network | NGFW, IPS, Antivirus | Hardware |
| Windows Defender | Host | Application & port filtering | Windows |
| iptables / ufw | Host | Packet filtering, NAT | Linux |
| ModSecurity | Application | Web traffic filtering | Linux/Windows |
| AWS WAF | Cloud | HTTP/S traffic filtering | Cloud |

---

## Firewall Configuration Basics

### Rules and Policies
- Define what traffic is **allowed or blocked**.
- Include **source IP, destination IP, port, protocol**.

### Zones and Interfaces
- Group interfaces into **trusted, untrusted, or DMZ zones**.
- Traffic control can be applied **between zones**.

### Logging and Monitoring
- Firewalls can **log blocked and allowed traffic**.
- Helps in **detecting attacks** and auditing network activity.

---

## Best Practices
1. Use **default-deny policy** (block all, allow only necessary traffic).  
2. Regularly **update firewall software/firmware**.  
3. Enable **logging** and monitor logs frequently.  
4. Configure **separate zones for internal, external, and DMZ networks**.  
5. Avoid placing unnecessary services in DMZ.  
6. Use **host-based firewalls** on critical systems in addition to network firewalls.  

---

## Summary
- Firewalls are **essential for network security**.  
- They can be **network-based, host-based, application-level, or cloud-based**.  
- Modern firewalls (NGFW) provide **advanced inspection and prevention capabilities**.  
- Proper configuration, monitoring, and adherence to best practices are crucial for **effective protection**.  

---

## Example Commands

### Windows Defender Firewall
```powershell
# Check firewall status
Get-NetFirewallProfile

# Block a specific port (e.g., 80)
New-NetFirewallRule -DisplayName "Block HTTP" -Direction Inbound -LocalPort 80 -Protocol TCP -Action Block
````

### Linux ufw

```bash
# Enable firewall
sudo ufw enable

# Deny incoming HTTP traffic
sudo ufw deny 80/tcp

# Allow SSH
sudo ufw allow 22/tcp

# Check status
sudo ufw status verbose
```

### Linux iptables

```bash
# Block all incoming traffic except SSH
sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT
sudo iptables -A INPUT -j DROP

# Save rules
sudo iptables-save > /etc/iptables/rules.v4