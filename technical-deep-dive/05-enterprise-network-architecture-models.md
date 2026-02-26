# Technical Deep Dive 05 – Enterprise Network Architecture Models

This document explains common enterprise network structures and their relevance to secure simulation hosting.

---

# 1️⃣ Traditional Enterprise Model

Internal Network (Private)
→ Firewall
→ DMZ (Demilitarized Zone)
→ Internet

---

# 2️⃣ DMZ Concept

DMZ hosts externally accessible services.

Purpose:
- Isolate public-facing systems
- Prevent direct access to internal network
- Contain compromise impact

Simulation hosting should be placed in isolated zone,
not internal production network.

---

# 3️⃣ Cloud Model (VPC-Based)

Modern architecture often uses:

VPC (Virtual Private Cloud)
- Public Subnet
- Private Subnet
- Security Groups
- Network ACLs

Landing page server:
→ Public subnet
→ Restricted inbound rules
→ No direct internal access

---

# 4️⃣ Segmentation Principles

- Least privilege network access
- Separation of duties
- Controlled ingress/egress
- Monitoring enabled

---

# 5️⃣ Applied Reflection

Proper network segmentation:

- Reduces blast radius
- Simplifies decommissioning
- Prevents cross-environment contamination
- Improves governance compliance

Enterprise architecture thinking is critical for security operations.
