# Technical Deep Dive 03 – NAT & Firewall

This document explores Network Address Translation (NAT) and firewall concepts relevant to simulation hosting and enterprise environments.

---

# 1️⃣ NAT (Network Address Translation)

NAT translates private IP addresses into public IP addresses.

Purpose:
- Preserve public IP space
- Hide internal network structure
- Enable outbound connectivity

## How NAT Works

Internal device (192.168.x.x)
→ NAT gateway
→ Public IP assigned
→ Internet

Return traffic is mapped back to the correct internal device.

---

# 2️⃣ Types of NAT

- Static NAT (one-to-one mapping)
- Dynamic NAT (pool-based mapping)
- PAT (Port Address Translation – many-to-one)

Most enterprises use PAT for outbound traffic.

---

# 3️⃣ Security Implications

Pros:
- Obscures internal IP addresses.
- Reduces direct inbound exposure.

Cons:
- Not a true security control.
- Requires firewall policies for protection.

---

# 4️⃣ Firewall Concepts

Firewall controls traffic based on rules.

Types:
- Stateless firewall
- Stateful firewall

Stateful firewalls track session state (e.g., TCP connections).

---

# 5️⃣ Firewall Rules

Common controls:
- Allow inbound 443 (HTTPS)
- Block unnecessary management ports
- Restrict outbound traffic

For simulation hosting:
- Only necessary ports exposed.
- Management access restricted by IP.

---

# 6️⃣ Applied Reflection

Proper NAT and firewall configuration reduces:
- Unintended exposure
- Lateral movement risk
- Infrastructure misconfiguration impact
