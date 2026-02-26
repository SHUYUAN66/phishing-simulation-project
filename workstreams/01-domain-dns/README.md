# Workstream 01 – Domain & DNS Management

This workstream covers domain lifecycle management and DNS configuration
for the internal phishing simulation.

It focuses on isolation, reputation control, and operational safety.

---

# 1️⃣ Executive Summary (Non-Technical)

A dedicated simulation domain is used to:

- Improve realism of the campaign.
- Avoid impacting the production corporate domain.
- Maintain clear separation between simulation and business systems.

DNS ensures that when a user clicks the link, the domain resolves
to the isolated hosting server.

---

# 2️⃣ Technical Responsibilities

## Domain Registration

- Register dedicated simulation domain.
- Avoid using primary corporate domain.
- Document ownership and lifecycle.
- Define decommission timeline after campaign.

## DNS Configuration

Typical records involved:

- A / AAAA record → maps domain to hosting IP.
- CNAME (if subdomain used).
- MX (if domain used for sending mail).
- SPF / DKIM / DMARC (if email authentication required).

DNS flow during click:

User Browser  
→ Recursive Resolver  
→ Authoritative DNS  
→ Returns Hosting IP  
→ Connects to Web Server

---

# 3️⃣ Design Decisions & Trade-offs

## Decision 1 – Separate Simulation Domain

Reason:
- Protect production domain reputation.
- Avoid accidental email blacklisting.
- Easier decommissioning.

Alternative:
- Use subdomain of corporate domain.

Trade-off:
- Subdomain increases reputational coupling.

---

## Decision 2 – Controlled DNS TTL

Reason:
- Faster correction if misconfiguration occurs.
- Easier rollback.

Trade-off:
- Lower TTL increases DNS query frequency.

---

# 4️⃣ Risk Considerations

## Risk: Domain Blacklisting

Cause:
- High click traffic.
- Suspicious reputation signals.

Mitigation:
- Controlled campaign size.
- Short campaign duration.
- Monitoring domain reputation status.

---

## Risk: Misconfigured DNS

Cause:
- Incorrect IP mapping.
- Expired domain.
- Missing records.

Mitigation:
- Pre-campaign validation.
- Test from multiple networks.
- Documented rollback plan.

---

# 5️⃣ Governance Controls

- Domain registration approved by Security.
- DNS changes documented.
- Access restricted to authorised administrators.
- Decommission plan defined post-campaign.

---

# 6️⃣ Deliverables

- Domain registration record.
- DNS configuration documentation.
- Validation checklist.
- Decommission report.

---

# 7️⃣ Interview Deep-Dive Hooks

Infrastructure Focus:
- Explain DNS resolution path during user click.

Cloud Focus:
- How to isolate hosting IP from internal network.

Security Focus:
- How to prevent reputation damage to corporate domain.

GRC Focus:
- Who approves domain lifecycle?
- How long should simulation domains be retained?
