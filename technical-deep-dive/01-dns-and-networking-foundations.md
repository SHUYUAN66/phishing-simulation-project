# Technical Deep Dive 01 – DNS & Networking Foundations

This document expands on the DNS and networking concepts that underpin the phishing simulation architecture.

The goal is not theoretical coverage, but applied engineering understanding.

---

# 1️⃣ Why DNS Matters in This Project

When a user clicks a simulation link:

Browser → DNS Resolution → Hosting IP → Web Server

If DNS is misconfigured:
- Landing page becomes unreachable.
- Campaign fails operationally.
- Risk of reputational or trust impact.

DNS is not just configuration; it is a reliability dependency.

---

# 2️⃣ DNS Resolution Flow (Applied View)

Simplified sequence:

1. User enters or clicks domain.
2. Local recursive resolver checks cache.
3. If cache expired, recursive resolver queries:
   - Root server
   - TLD server
   - Authoritative name server
4. Authoritative server returns A/AAAA record.
5. Resolver caches result (based on TTL).
6. Browser connects to returned IP.

Key insight:
The authoritative server is the source of truth.
Recursive resolvers perform iterative lookups on behalf of the client.

---

# 3️⃣ TTL (Time To Live) – Design Considerations

TTL determines how long DNS responses are cached.

## Short TTL

Pros:
- Faster rollback in case of misconfiguration.
- Easier to change hosting IP.

Cons:
- Higher DNS query volume.
- Slightly increased infrastructure load.

## Long TTL

Pros:
- Reduced DNS traffic.
- Stable caching behaviour.

Cons:
- Slower correction if IP changes.
- Delayed recovery if configuration error occurs.

### Applied Decision in Simulation Context

Moderate TTL preferred.

Reason:
Simulation infrastructure may need quick rollback,
but high query volume is typically limited due to campaign scope.

---

# 4️⃣ DNS Propagation – What It Actually Means

Propagation delay is not “slow spreading.”

It results from:
- Cached records in recursive resolvers.
- TTL expiry timing differences.
- Geographic resolver variations.

Implication:
DNS updates may appear inconsistent across regions until cache expiry.

Engineering takeaway:
Never assume instant global update.

---

# 5️⃣ Domain Reputation & Blacklisting (High-Level)

Enterprise mail gateways and security tools reference:

- Reputation databases.
- Threat intelligence feeds.
- Behavioural anomaly signals.

Factors influencing reputation:
- Sudden mail spikes.
- Suspicious link patterns.
- External reports.

Design mitigation:
- Use isolated simulation domain.
- Control campaign size.
- Limit active campaign duration.
- Decommission domain post-use.

---

# 6️⃣ Networking Fundamentals Required

This project relies on core networking principles.

## A. TCP vs UDP

DNS typically uses UDP (port 53).
HTTP/HTTPS uses TCP.
SMTP uses TCP.

Understanding transport protocols helps reason about reliability and behaviour.

---

## B. TCP Three-Way Handshake (High-Level)

1. SYN
2. SYN-ACK
3. ACK

Ensures reliable session establishment before HTTP request.

Applied Insight:
Landing page availability depends on successful TCP connection establishment.

---

## C. HTTPS & TLS

HTTPS = HTTP over TLS.

TLS provides:
- Encryption
- Integrity
- Server authentication (certificate validation)

Simulation landing pages must enforce HTTPS to:
- Prevent browser warnings.
- Maintain trust.
- Avoid user suspicion.

---

## D. Network Isolation Concepts

Hosting environment should:

- Not reside in internal production network.
- Use controlled inbound access.
- Restrict management ports.
- Separate simulation from business systems.

This reduces blast radius.

---

# 7️⃣ Design Reflection

DNS and networking are often invisible layers.

However, they directly affect:

- Reliability
- Risk containment
- User trust
- Incident management

Security engineering is not only about detection,
but about understanding infrastructure dependencies.

---

# 8️⃣ Interview Deep-Dive Hooks

Infrastructure:
- Explain recursive vs authoritative servers.

Security:
- How domain reputation affects email delivery.

Cloud:
- How TTL settings influence rollback capability.

SOC:
- How DNS misconfiguration could appear as incident signal.
