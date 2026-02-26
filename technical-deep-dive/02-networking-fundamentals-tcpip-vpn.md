# Technical Deep Dive 02 – Networking Fundamentals (TCP/IP & VPN)

This document explains foundational networking concepts required to understand the phishing simulation infrastructure.

The focus is applied understanding rather than theoretical memorisation.

---

# 1️⃣ TCP/IP Model (Applied View)

The TCP/IP model consists of four layers:

| Layer | Responsibility | Examples |
|--------|---------------|----------|
| Application | Application protocols | HTTP, SMTP, DNS |
| Transport | Reliable / unreliable delivery | TCP, UDP |
| Internet | Addressing & routing | IP |
| Network Interface | Physical transmission | Ethernet |

In this project:
- HTTP serves landing pages.
- SMTP delivers emails.
- DNS resolves domains.
- TCP ensures reliable communication.

---

# 2️⃣ IP Addressing & Routing

IP is responsible for delivering packets to the correct host.

## Public vs Private IP

Private ranges:
- 10.0.0.0/8
- 172.16.0.0–172.31.255.255
- 192.168.0.0/16

Hosting servers require public IPs.
Enterprise endpoints often use private IPs behind NAT.

---

# 3️⃣ TCP – Reliable Transport

TCP ensures:
- Ordered delivery
- Retransmission
- Congestion control
- Flow control

## Three-Way Handshake

1. SYN  
2. SYN-ACK  
3. ACK  

This establishes a reliable session before HTTP data transfer.

Applied Insight:
Landing page availability depends on successful TCP handshake.

---

# 4️⃣ UDP – Lightweight Transport

UDP:
- Connectionless
- No retransmission guarantee
- Faster but less reliable

DNS typically uses UDP.

---

# 5️⃣ VPN (Virtual Private Network)

VPN creates an encrypted tunnel over public networks.

Purpose:
- Secure remote access
- Protect data confidentiality
- Simulate internal network presence

Types:
- Remote Access VPN
- Site-to-Site VPN
- SSL VPN
- IPSec VPN

In enterprise scenarios, remote users may access email via VPN,
affecting IP logging and event correlation.

---

# 6️⃣ Engineering Reflection

Understanding TCP/IP allows:

- Diagnosing delivery issues
- Interpreting log sources
- Understanding latency causes
- Evaluating infrastructure reliability

Networking is foundational to security engineering.
