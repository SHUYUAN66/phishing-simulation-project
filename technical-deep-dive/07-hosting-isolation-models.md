# Technical Deep Dive 03 – Hosting Isolation Models

This document explores hosting isolation strategies for phishing simulation infrastructure.

The goal is to demonstrate architectural risk containment thinking.

---

# 1️⃣ Problem Context

A simulation landing page must be:

- Publicly accessible
- Reliable
- Controlled
- Isolated from production systems

The key question:

How should hosting be designed to minimise risk?

---

# 2️⃣ Hosting Model Options

## Option 1 – Host Within Corporate Production Infrastructure

Example:
Host simulation site on existing internal web server.

Pros:
- Easier management
- No additional infrastructure cost
- Centralised logging

Cons:
- High blast radius if misconfigured
- Potential production contamination
- Risk of reputational damage to primary domain
- Internal system exposure

Risk Level: High

---

## Option 2 – Dedicated Server Within Corporate Network (Segmented)

Example:
Host on isolated VLAN or DMZ server.

Pros:
- Some network segmentation
- Controlled internal access
- Easier policy alignment

Cons:
- Still within corporate trust boundary
- Potential lateral movement risk
- Shared operational dependencies

Risk Level: Medium

---

## Option 3 – Isolated Cloud Hosting (Recommended)

Example:
Dedicated cloud VM or container in separate VPC/subnet.

Pros:
- Clear isolation boundary
- Reduced blast radius
- Easier decommission
- Independent scaling
- No direct internal network exposure

Cons:
- Additional configuration complexity
- Separate monitoring setup required

Risk Level: Low (when configured properly)

---

# 3️⃣ Isolation Layers Explained

Isolation should exist at multiple layers:

## A. Network Isolation
- Separate VPC or subnet
- Controlled inbound ports
- No internal network routing

## B. Identity Isolation
- Separate credentials
- Limited administrative access

## C. Domain Isolation
- Dedicated simulation domain
- Not tied to production domain

## D. Logging Isolation
- Logs stored separately
- Access restricted

---

# 4️⃣ Blast Radius Concept

Blast radius = potential impact scope if system compromised.

Production hosting:
→ Blast radius includes internal services.

Isolated cloud hosting:
→ Blast radius limited to simulation environment only.

Security engineering prioritises blast radius reduction.

---

# 5️⃣ Cloud-Based Isolation Model (Applied Example)

Recommended structure:

Internet
→ Public Subnet (Landing Page Server)
→ Security Group allows 443 only
→ No direct route to internal network
→ Separate management subnet

Additional controls:
- No SSH open to world
- Key-based access
- Monitoring enabled
- Decommission after campaign

---

# 6️⃣ Scalability Considerations

If scaling to large enterprise:

- Load balancer in front of landing page
- Auto-scaling group
- Rate limiting
- Logging pipeline integration

Isolation must remain intact even under scale.

---

# 7️⃣ Governance Considerations

- Hosting approval documented
- Access logs retained
- Infrastructure lifecycle defined
- Decommission plan executed post-campaign

---

# 8️⃣ Engineering Reflection

Hosting decisions determine:

- Risk containment
- Reputation exposure
- Operational stability
- Trust preservation

Security simulation must prioritise containment over convenience.

---

# 🔎 Interview Deep-Dive Hooks

Infrastructure:
- Explain blast radius reduction.

Cloud:
- Compare VPC isolation vs on-prem DMZ.

Security:
- Why simulation should not reside in production network.

GRC:
- Why infrastructure lifecycle documentation matters.
