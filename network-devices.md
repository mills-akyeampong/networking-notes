# Network Devices

> **Author**: Mills Kojo Akyeampong  
> **Role**: Security Systems & Network Engineer    
> **Intended Audience**: Networking students, professionals, self-learners

---

## Table of Contents
- [Network Devices](#network-devices)
  - [Table of Contents](#table-of-contents)
  - [Introduction](#introduction)
  - [Hub](#hub)
  - [Switch](#switch)
  - [Router](#router)
  - [Access Point (AP)](#access-point-ap)
  - [Firewall](#firewall)
  - [Gateway](#gateway)
  - [Modem](#modem)
  - [Network Interface Card (NIC)](#network-interface-card-nic)
  - [Conclusion](#conclusion)

---

## Introduction
Network devices are essential components that allow computers, servers, and other endpoints to communicate in a network. Each device plays a specific role in managing, securing, or facilitating data transmission.

---

## Hub
- **Definition:** A basic device that connects multiple computers in a network.  
- **Function:** Broadcasts data to all connected devices.  
- **Limitation:** Inefficient because every packet is sent to every port.  
- **Layer:** Operates at the **Physical Layer (Layer 1)**.  
- **Use Case:** Rarely used today; replaced by switches.

---

## Switch
- **Definition:** A device that connects multiple devices and forwards data only to the intended recipient.  
- **Function:** Uses **MAC addresses** to determine the destination of frames.  
- **Layer:** Operates at **Data Link Layer (Layer 2)**, some advanced switches also work at **Layer 3**.  
- **Use Case:** Common in LANs for efficient communication.

---

## Router
- **Definition:** A device that forwards packets between different networks.  
- **Function:** Uses **IP addresses** to determine the best path.  
- **Layer:** Operates at the **Network Layer (Layer 3)**.  
- **Use Case:** Connects a home/office LAN to the internet.

---

## Access Point (AP)
- **Definition:** A device that allows wireless devices to connect to a wired network.  
- **Function:** Provides **Wi-Fi connectivity**.  
- **Layer:** Operates at **Layer 2 (Data Link Layer)**.  
- **Use Case:** Extending wireless coverage in homes, offices, and public spaces.

---

## Firewall
- **Definition:** A security device that monitors and controls network traffic based on rules.  
- **Function:** Protects the network by filtering **unauthorized access**.  
- **Types:** Hardware firewall, software firewall, next-generation firewall (NGFW).  
- **Layer:** Operates from **Layer 3 to Layer 7** depending on type.  
- **Use Case:** Essential in enterprise networks for cybersecurity.

---

## Gateway
- **Definition:** A device that acts as a "translator" between networks using different protocols.  
- **Function:** Converts data so that different systems can communicate.  
- **Layer:** Can operate at multiple layers depending on implementation.  
- **Use Case:** Connecting enterprise networks to external systems.

---

## Modem
- **Definition:** A device that converts **digital signals** to **analog signals** and vice versa.  
- **Function:** Enables internet connectivity over telephone lines, DSL, or cable.  
- **Layer:** Operates at **Layer 1 (Physical Layer)**.  
- **Use Case:** ISPs use modems to deliver internet to subscribers.

---

## Network Interface Card (NIC)
- **Definition:** A hardware component inside a computer or server that allows it to connect to a network.  
- **Function:** Provides both **wired (Ethernet)** and **wireless (Wi-Fi)** connectivity.  
- **Layer:** Operates at **Layer 2 (Data Link Layer)**.  
- **Use Case:** Every networked device requires a NIC.

---

## Conclusion
Each network device has a unique role in establishing, managing, and securing communication within a network. Together, they form the backbone of modern networking, ensuring efficient and secure data transmission.

