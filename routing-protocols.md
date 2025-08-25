# Routing Protocols

> **Author**: Mills Kojo Akyeampong  
> **Role**: Security Systems & Network Engineer    
> **Intended Audience**: Networking students, professionals, self-learners

---

## 📚 Table of Contents

- [Routing Protocols](#routing-protocols)
  - [📚 Table of Contents](#-table-of-contents)
  - [📖 Introduction](#-introduction)
  - [🧭 What Is a Routing Protocol?](#-what-is-a-routing-protocol)
  - [🛣️ Types of Routing](#️-types-of-routing)
    - [1. Static Routing](#1-static-routing)
    - [2. Dynamic Routing](#2-dynamic-routing)
  - [🗂️ Classification of Routing Protocols](#️-classification-of-routing-protocols)
    - [1. Distance Vector Routing Protocols](#1-distance-vector-routing-protocols)
    - [2. Link State Routing Protocols](#2-link-state-routing-protocols)
    - [3. Hybrid Routing Protocols](#3-hybrid-routing-protocols)
  - [🌍 Interior vs Exterior Routing Protocols](#-interior-vs-exterior-routing-protocols)
  - [🚦 Popular Routing Protocols](#-popular-routing-protocols)
  - [📊 Comparison Table](#-comparison-table)
  - [📏 Routing Metrics](#-routing-metrics)
  - [🔢 Administrative Distance (AD)](#-administrative-distance-ad)
  - [❓ FAQs](#-faqs)
    - [Q1: Why not use only static routing?](#q1-why-not-use-only-static-routing)
    - [Q2: What happens if multiple protocols offer a route?](#q2-what-happens-if-multiple-protocols-offer-a-route)
    - [Q3: Can I use multiple routing protocols together?](#q3-can-i-use-multiple-routing-protocols-together)
    - [Q4: Is BGP used in private networks?](#q4-is-bgp-used-in-private-networks)
  - [✅ Conclusion](#-conclusion)
  - [📊 Visual Diagram: Routing Protocol Classification](#-visual-diagram-routing-protocol-classification)
  - [🧾 Routing Protocols Cheat Sheet](#-routing-protocols-cheat-sheet)

---

## 📖 Introduction

In computer networks, **routing** is the process of selecting the best path for data to travel from source to destination.  
**Routing protocols** help routers dynamically learn, share, and update information about network paths.

---

## 🧭 What Is a Routing Protocol?

A **routing protocol** is a set of rules used by routers to communicate with each other, exchange routing information, and determine the **best path** for forwarding packets.

---

## 🛣️ Types of Routing

### 1. Static Routing

- Routes are **manually configured** by a network administrator.
- **No automatic updates**.
- Simple, but not scalable.

### 2. Dynamic Routing

- Routers **automatically discover and maintain routes** using routing protocols.
- Adapts to network changes.
- Ideal for **large and complex networks**.

---

## 🗂️ Classification of Routing Protocols

### 1. Distance Vector Routing Protocols

- Use **hop count** to determine the best path.
- Routers **periodically broadcast** their entire routing table.
- **Slow convergence**, risk of **routing loops**.

🔹 Examples:
- **RIP (Routing Information Protocol)**
- **IGRP (Interior Gateway Routing Protocol)**

---

### 2. Link State Routing Protocols

- Build a **complete map of the network** (topology).
- Use **Dijkstra’s algorithm** to calculate the shortest path.
- **Faster convergence**, more scalable and accurate.

🔹 Examples:
- **OSPF (Open Shortest Path First)**
- **IS-IS (Intermediate System to Intermediate System)**

---

### 3. Hybrid Routing Protocols

- Combine features of **distance vector** and **link-state** protocols.
- Efficient and scalable.

🔹 Example:
- **EIGRP (Enhanced Interior Gateway Routing Protocol)**

---

## 🌍 Interior vs Exterior Routing Protocols

| Type | Description | Protocols |
|------|-------------|-----------|
| **IGP (Interior Gateway Protocol)** | Used within a single autonomous system (AS) | RIP, OSPF, EIGRP |
| **EGP (Exterior Gateway Protocol)** | Used to exchange routing info between different ASes | **BGP (Border Gateway Protocol)** |

---

## 🚦 Popular Routing Protocols

| Protocol | Type | Algorithm | Key Features |
|----------|------|-----------|--------------|
| **RIP** | Distance Vector | Bellman-Ford | Max 15 hops, simple, legacy |
| **IGRP** | Distance Vector | Cisco proprietary | Supports multiple metrics |
| **EIGRP** | Hybrid | Diffusing Update Algorithm (DUAL) | Fast convergence, Cisco proprietary |
| **OSPF** | Link-State | Dijkstra (SPF) | Open standard, supports areas |
| **IS-IS** | Link-State | Dijkstra | Used in large ISPs |
| **BGP** | Path Vector (EGP) | Best Path Selection | Used on the Internet, scalable |

---

## 📊 Comparison Table

| Feature       | RIP       | OSPF      | EIGRP     | BGP        |
|---------------|-----------|-----------|-----------|------------|
| Type          | IGP       | IGP       | IGP       | EGP        |
| Algorithm     | Distance Vector | Link State | Hybrid     | Path Vector |
| Metric        | Hop Count | Cost      | Bandwidth, delay, etc. | Path attributes |
| Max Hops      | 15        | Unlimited | 224       | Unlimited  |
| Convergence   | Slow      | Fast      | Very Fast | Slow       |
| Scalability   | Low       | High      | Medium    | Very High  |
| Open Standard | Yes       | Yes       | No (Cisco) | Yes        |

---

## 📏 Routing Metrics

Routing decisions are often based on **metrics**, including:

- **Hop count**
- **Bandwidth**
- **Delay (latency)**
- **Load**
- **Reliability**
- **MTU (Maximum Transmission Unit)**
- **Cost (in OSPF)**

---

## 🔢 Administrative Distance (AD)

**Administrative Distance** = trustworthiness of a routing source (lower = more trusted)

| Source           | AD Value |
|------------------|----------|
| Connected route  | 0        |
| Static route     | 1        |
| EIGRP            | 90       |
| OSPF             | 110      |
| RIP              | 120      |
| External BGP     | 20       |
| Internal BGP     | 200      |
| Unknown          | 255 (invalid) |

---

## ❓ FAQs

### Q1: Why not use only static routing?

- Static routing doesn't adapt to changes (e.g., link failures).
- It's hard to manage in large networks.

### Q2: What happens if multiple protocols offer a route?

- The router chooses the route with the **lowest AD**.

### Q3: Can I use multiple routing protocols together?

- ✅ Yes, but you must manage **route redistribution** carefully.

### Q4: Is BGP used in private networks?

- Not commonly. BGP is mainly for **Internet-scale** routing between ISPs.

---

## ✅ Conclusion

Routing protocols are essential to ensure data finds the most efficient and reliable path across networks.  
They dynamically adapt to changes, reduce administrative burden, and scale to support modern enterprise and Internet infrastructure.

🎯 **In summary:**

- Use **IGPs (like OSPF/EIGRP)** within your organization.
- Use **BGP** for communication between ISPs or large-scale networks.
- Understand **metrics**, **AD**, and **routing types** to optimize performance and security.


---

## 📊 Visual Diagram: Routing Protocol Classification

```mermaid
graph TD
    A[Routing Protocols] --> B[Interior Gateway Protocols (IGPs)]
    A --> C[Exterior Gateway Protocols (EGPs)]

    B --> D[Distance Vector]
    B --> E[Link State]
    B --> F[Hybrid]

    D --> G[RIP]
    D --> H[IGRP]

    E --> I[OSPF]
    E --> J[IS-IS]

    F --> K[EIGRP]

    C --> L[BGP]
```

> **Note**: You can embed this Mermaid diagram directly in GitHub markdown or render it using tools like Obsidian, Typora, or VS Code with Mermaid support.

---

## 🧾 Routing Protocols Cheat Sheet

| Category        | Protocol | Type | Metric Used                         | Max Hops | AD     | Open Standard | Notes                          |
| --------------- | -------- | ---- | ----------------------------------- | -------- | ------ | ------------- | ------------------------------ |
| Distance Vector | RIP      | IGP  | Hop Count                           | 15       | 120    | ✅ Yes         | Simple, slow convergence       |
| Distance Vector | IGRP     | IGP  | Bandwidth, Delay                    | 100      | 100    | ❌ Cisco only  | Legacy, replaced by EIGRP      |
| Link-State      | OSPF     | IGP  | Cost (Bandwidth)                    | ∞        | 110    | ✅ Yes         | Area support, fast convergence |
| Link-State      | IS-IS    | IGP  | Cost                                | ∞        | 115    | ✅ Yes         | Used by ISPs                   |
| Hybrid          | EIGRP    | IGP  | Bandwidth, Delay, Load, Reliability | 224      | 90     | ❌ Cisco only  | Combines DV + LS               |
| Path Vector     | BGP      | EGP  | Path Attributes                     | ∞        | 20/200 | ✅ Yes         | Internet routing protocol      |

---
