# MAC Addressgit

## Table of Contents
- [MAC Addressgit](#mac-addressgit)
  - [Table of Contents](#table-of-contents)
  - [1. What is a MAC Address?](#1-what-is-a-mac-address)
  - [2. Why do we need MAC addresses? (Layer context)](#2-why-do-we-need-mac-addresses-layer-context)
  - [3. Format \& Notation](#3-format--notation)
  - [4. Bit-level anatomy (I/G and U/L bits)](#4-bit-level-anatomy-ig-and-ul-bits)
  - [5. Types of MAC addresses](#5-types-of-mac-addresses)
  - [6. Special \& reserved MAC ranges you should know](#6-special--reserved-mac-ranges-you-should-know)
  - [7. Step-by-step: How frames are delivered on a LAN](#7-step-by-step-how-frames-are-delivered-on-a-lan)
    - [7.1 Same VLAN / Same Subnet](#71-same-vlan--same-subnet)
    - [7.2 Different Subnet (via Default Gateway)](#72-different-subnet-via-default-gateway)
  - [8. How switches use MAC addresses (CAM tables)](#8-how-switches-use-mac-addresses-cam-tables)
  - [9. ARP \& Neighbor Discovery (mapping IP ⇄ MAC)](#9-arp--neighbor-discovery-mapping-ip--mac)
  - [10. EUI-64 \& IPv6 interface IDs](#10-eui-64--ipv6-interface-ids)
  - [11. Locally administered \& randomized MACs](#11-locally-administered--randomized-macs)
  - [12. Virtualization \& cloud considerations](#12-virtualization--cloud-considerations)
  - [13. Security considerations](#13-security-considerations)
  - [14. How to find your MAC address (common OSes)](#14-how-to-find-your-mac-address-common-oses)
  - [15. Troubleshooting tips \& common pitfalls](#15-troubleshooting-tips--common-pitfalls)
  - [16. Quick FAQ / Interview-style checks](#16-quick-faq--interview-style-checks)

---

## 1. What is a MAC Address?
A **MAC (Media Access Control) address** is a **Layer 2** hardware identifier assigned to a network interface controller (NIC). It uniquely identifies an interface on a local network segment (e.g., Ethernet or Wi-Fi).

- Standard length: **48 bits** (6 bytes) → often called **EUI-48**.
- Typical look: `00:1A:2B:3C:4D:5E` or `00-1A-2B-3C-4D-5E`.

> Think: IP tells you **where** to go (Layer 3), MAC tells you **who** on the local link.

---

## 2. Why do we need MAC addresses? (Layer context)
- **Ethernet/Wi-Fi frames** use MACs to deliver data **within the same broadcast domain/VLAN**.
- **Routers** forward between IP subnets; but on each local link, the **frame’s destination MAC** must match the next-hop interface.
- Without MACs, devices wouldn’t know which local NIC should actually receive a frame.

---

## 3. Format & Notation
- **48 bits** split into two logical halves:
  - **OUI** (Organizationally Unique Identifier): **first 24 bits** (first 3 bytes) → identifies the vendor.
  - **NIC-specific** portion: **last 24 bits** → assigned by the vendor (or system) to make the address unique.
- **Hexadecimal**, 8-bit chunks shown as two hex digits:
  - Example: `3C:5A:B4:12:34:56`
    - `3C-5A-B4` → OUI
    - `12-34-56` → device-specific
- Separators: colon `:`, hyphen `-`, or none (e.g., `3C5AB4123456`).

---

## 4. Bit-level anatomy (I/G and U/L bits)
Focus on the **first byte** (8 bits). The **least significant two bits** have special meanings:

- **I/G (Individual/Group) bit** → **bit 0** (LSB of first byte)
  - `0` = **Unicast** (individual device)
  - `1` = **Multicast/Group**
- **U/L (Universal/Local) bit** → **bit 1**
  - `0` = **Universally administered** (burned-in by vendor; matches OUI)
  - `1` = **Locally administered** (overridden or software-assigned)

Example (binary of first byte):
```

First byte:  00111100 (0x3C)
^^
||\_\_ I/G bit
|\_\_\_ U/L bit
Here: U/L=1? No (bit=0) → globally unique; I/G=0 → unicast

````

---

## 5. Types of MAC addresses
- **Unicast**: I/G=0 → identifies a single interface. Most device MACs.
- **Multicast**: I/G=1 → frames intended for a group. NICs can subscribe to specific multicast groups.
- **Broadcast**: All bits 1 → `FF:FF:FF:FF:FF:FF`. Every NIC on the LAN processes it.

---

## 6. Special & reserved MAC ranges you should know
- **Broadcast**: `FF:FF:FF:FF:FF:FF`
- **IPv4 Multicast mapping**: `01:00:5E:xx:xx:xx`
- **IPv6 Multicast mapping**: `33:33:xx:xx:xx:xx`
- **Spanning Tree Protocol (STP)**: `01:80:C2:00:00:00`
- **LLDP**: `01:80:C2:00:00:0E`
- **Cisco CDP**: `01:00:0C:CC:CC:CC`

---

## 7. Step-by-step: How frames are delivered on a LAN

### 7.1 Same VLAN / Same Subnet
**Goal:** Host A (IP `192.168.1.10`) sends to Host B (IP `192.168.1.20`) on VLAN 10.

1. **A checks its ARP cache** for `192.168.1.20` → if not found:
2. **A broadcasts ARP Request**: “Who has `192.168.1.20`? Tell `192.168.1.10`”  
   - **Dest MAC**: `FF:FF:FF:FF:FF:FF`  
   - **Src MAC**: A’s NIC MAC
3. **B receives** the ARP Request and **unicasts ARP Reply**:  
   - “`192.168.1.20` is at **B-MAC**”
4. **A updates ARP cache** with `192.168.1.20 → B-MAC`.
5. **A sends the frame**:  
   - **Dest MAC**: **B-MAC**  
   - **Src MAC**: A-MAC
6. **Switch forwards** the frame to B’s port.
7. **B receives** and processes the payload.

### 7.2 Different Subnet (via Default Gateway)
**Goal:** A (`192.168.1.10/24`, GW `192.168.1.1`) sends to `8.8.8.8`.

1. **A checks subnet** → sees `8.8.8.8` is outside local subnet.
2. **A ARPs for gateway’s IP** `192.168.1.1`.
3. **A builds frame**:  
   - **Dest MAC**: Gateway’s MAC  
   - **Src MAC**: A-MAC  
   - **IP Dest**: `8.8.8.8`
4. **Router forwards** packet with a new L2 header at each hop.

---

## 8. How switches use MAC addresses (CAM tables)
- **Learning**: Switch records the **source MAC** with the port it arrived on.
- **Forwarding**:  
  - If **dest MAC is known** → forward only on that port.  
  - If **unknown** → flood within VLAN.
- **Broadcasts** → always flooded within VLAN.
- **Aging**: Entries expire (default ~300s).

---

## 9. ARP & Neighbor Discovery (mapping IP ⇄ MAC)
- **ARP (IPv4)**: Broadcast request + unicast reply.
- **NDP (IPv6)**: Uses ICMPv6 multicast-based Neighbor Solicitation/Advertisement.

---

## 10. EUI-64 & IPv6 interface IDs
IPv6 interface IDs can be derived from MAC:
- Insert `FF:FE` in the middle.
- Flip the U/L bit of the first byte.

---

## 11. Locally administered & randomized MACs
- **U/L=1** → locally administered (manual or software-generated).
- Modern OSes **randomize Wi-Fi MACs** for privacy.

---

## 12. Virtualization & cloud considerations
- Hypervisors assign **virtual MACs** (often locally administered).
- Cloning VMs may cause **duplicate MAC conflicts**.
- Cloud NICs provide stable but virtual MACs.

---

## 13. Security considerations
- **MAC filtering** is weak; MACs can be spoofed.
- Use **802.1X**, **port security**, **Dynamic ARP Inspection**, and **DHCP snooping**.
- Monitor for **MAC flaps** or **ARP spoofing**.

---

## 14. How to find your MAC address (common OSes)

**Windows**
```bat
ipconfig /all
getmac /v
````

**Linux**

```bash
ip link show
```

**macOS**

```bash
ifconfig
```

**Cisco IOS**

```
show interfaces
show mac address-table
```

---

## 15. Troubleshooting tips & common pitfalls

* **Check ARP table** if same subnet devices can’t talk.
* **MAC flapping** → loop or duplicate MACs.
* **VLAN mismatch** → ARP requests don’t get replies.
* **Wi-Fi MAC randomization** may confuse captive portals.

---

## 16. Quick FAQ / Interview-style checks

* **How many bits in a MAC?** 48 bits.
* **Layer?** OSI Layer 2.
* **Broadcast MAC?** `FF:FF:FF:FF:FF:FF`.
* **MAC vs IP?** MAC = local delivery, IP = end-to-end.
* **I/G bit?** Unicast (0) vs Multicast (1).
* **U/L bit?** Universal (0) vs Local (1).
* **Routers forward broadcasts?** No.
