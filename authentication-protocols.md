# Authentication Protocols & Services

> **Author**: Mills Kojo Akyeampong  
> **Role**: Security Systems & Network Engineer    
> **Intended Audience**: Networking students, professionals, self-learners

---

## ​ Table of Contents

- [Authentication Protocols \& Services](#authentication-protocols--services)
  - [​ Table of Contents](#-table-of-contents)
  - [1. Introduction](#1-introduction)
  - [2. Key Authentication Protocols](#2-key-authentication-protocols)
    - [1. Kerberos](#1-kerberos)
    - [2. RADIUS (Remote Authentication Dial-In User Service)](#2-radius-remote-authentication-dial-in-user-service)
    - [3. TACACS+ (Terminal Access Controller Access-Control System Plus)](#3-tacacs-terminal-access-controller-access-control-system-plus)
    - [4. LDAP (Lightweight Directory Access Protocol)](#4-ldap-lightweight-directory-access-protocol)
    - [5. SAML (Security Assertion Markup Language)](#5-saml-security-assertion-markup-language)
    - [6. OAuth 2.0 \& OpenID Connect](#6-oauth-20--openid-connect)
    - [7. WebAuthn / FIDO2](#7-webauthn--fido2)
    - [8. EAP (Extensible Authentication Protocol)](#8-eap-extensible-authentication-protocol)
    - [9. SASL (Simple Authentication and Security Layer)](#9-sasl-simple-authentication-and-security-layer)
  - [Comparison Table](#comparison-table)
  - [Use Cases](#use-cases)
  - [Cheat Sheet](#cheat-sheet)
  - [Conclusion](#conclusion)

---

## 1. Introduction

Authentication protocols define how identities are verified and secured across networks. They underpin trust, access control, and security across services and applications.

---

## 2. Key Authentication Protocols

### 1. Kerberos  
- Ticket-based, centralized authentication using a Key Distribution Center (KDC)  
- Supports **single sign-on (SSO)** and mutual authentication  
- Requires time synchronization; vulnerability includes KDC as single point of failure :contentReference[oaicite:5]{index=5}

### 2. RADIUS (Remote Authentication Dial-In User Service)  
- Offers **Authentication, Authorization, and Accounting (AAA)**  
- Client-server model, typically used for network access (Wi‑Fi, VPN)  
- Supports PAP, CHAP, EAP methods; responses include Access-Accept/Reject/Challenge :contentReference[oaicite:6]{index=6}

### 3. TACACS+ (Terminal Access Controller Access-Control System Plus)  
- Cisco proprietary AAA protocol  
- Uses TCP; encrypts entire packet body; separates AAA functions for granular control :contentReference[oaicite:7]{index=7}

### 4. LDAP (Lightweight Directory Access Protocol)  
- Directory service protocol used for managing and querying user credentials  
- Commonly used with AD and enterprise authentication flows :contentReference[oaicite:8]{index=8}

### 5. SAML (Security Assertion Markup Language)  
- XML-based authentication for web SSO  
- Involves Identity Provider (IdP) issuing assertion to Service Provider (SP) after user authentication :contentReference[oaicite:9]{index=9}

### 6. OAuth 2.0 & OpenID Connect  
- OAuth 2.0 handles authorization; OpenID Connect adds identity layer for authentication and profile info  
- Enables federated access and SSO :contentReference[oaicite:10]{index=10}

### 7. WebAuthn / FIDO2  
- Passwordless, strong authentication using public-key cryptography via hardware or platform authenticators  
- Resistant to phishing and malware :contentReference[oaicite:11]{index=11}

### 8. EAP (Extensible Authentication Protocol)  
- Framework supporting various authentication methods for network access (Wi‑Fi, VPN)  
- Methods include EAP-TLS, PEAP, TTLS, often integrated with RADIUS :contentReference[oaicite:12]{index=12}

### 9. SASL (Simple Authentication and Security Layer)  
- Framework decoupling authentication methods from application protocols (e.g., SMTP, LDAP)  
- Supports authentication and optional data integrity/confidentiality :contentReference[oaicite:13]{index=13}

---

##  Comparison Table

| Protocol / Framework | Type           | Use Case                | Pros                                  | Cons                              |
|----------------------|----------------|--------------------------|----------------------------------------|-----------------------------------|
| Kerberos             | Ticket-based   | Enterprise SSO           | SSO, mutual auth; robust                | Time sync, KDC dependency         |
| RADIUS               | AAA client/server | Network access        | Centralized, widely supported           | Partial encryption, UDP-based     |
| TACACS+              | AAA client/server | Device admin           | Full packet encryption, granular AAA    | Cisco proprietary, TCP overhead   |
| LDAP                 | Directory      | Account lookup/auth      | Centralized directory                   | Not an auth protocol per se       |
| SAML                 | SSO federation | Web-based SSO            | Secure, cross-domain SSO                | XML complexity                    |
| OAuth2 / OIDC        | Auth / Identity | Web / API access        | Modern, token-based                     | Access vs auth separation         |
| WebAuthn / FIDO2     | Public-key     | Passwordless login       | Phishing-resistant, secure              | Requires hardware or platform     |
| EAP                  | Auth framework | Wi‑Fi / 802.1X           | Flexible, secure                        | Complex, needs backend            |
| SASL                 | Auth framework | App protocols (SMTP, etc.) | Protocol-agnostic                      | Depends on underlying mechanism   |

---

##  Use Cases

- **Enterprise Domain**: Kerberos for Windows AD environments  
- **Wi‑Fi / VPN Access**: EAP with RADIUS  
- **Network Device Control**: TACACS+ for granular command-level authorization  
- **Web Portals / SSO**: SAML or OpenID Connect for secure web sign-ons  
- **Modern Web Authentication**: WebAuthn for passwordless user login

---

##  Cheat Sheet

| Protocol              | Role / Use                           | Key Feature                    |
|-----------------------|--------------------------------------|--------------------------------|
| Kerberos              | SSO, mutual auth                     | Tickets, KDC-based             |
| RADIUS                | Network access AAA                   | Centralized, supports EAP      |
| TACACS+               | Device admin AAA                     | Full encryption, TCP-based     |
| LDAP                  | Directory & credential lookup        | Centralized directory access   |
| SAML                  | Web SSO federation                   | XML assertion exchange         |
| OAuth2 / OIDC         | Authorization & authentication       | Token-based, API-friendly      |
| WebAuthn / FIDO2      | Passwordless strong auth             | Crypto-backed, phishing-resistant |
| EAP                   | Network access framework             | Flexible method support        |
| SASL                  | Auth for application protocols       | Protocol-agnostic layer        |

---

##  Conclusion

Authentication protocols span a broad spectrum—from traditional ticket-based (Kerberos) and AAA systems (RADIUS, TACACS+) to modern SSO frameworks (SAML, OAuth/OIDC) and secure passwordless standards (WebAuthn). Choosing the right one depends on your environment, security needs, and scalability. Let me know if you'd like configuration examples or deeper breakdown for any specific protocol!

