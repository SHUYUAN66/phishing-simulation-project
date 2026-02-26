# Technical Deep Dive 04 – Tokenisation & Data Minimisation

This document explores how identity tracking and behavioural logging
can be implemented responsibly in phishing simulation environments.

The focus is balancing measurement accuracy with ethical and privacy boundaries.

---

# 1️⃣ Problem Context

Phishing simulation requires behavioural tracking:

- Who clicked?
- When did they click?
- Did they interact?

However, directly storing user identity or raw credentials
introduces privacy, ethical, and compliance risks.

Key engineering challenge:

How do we measure behaviour without over-collecting sensitive data?

---

# 2️⃣ Tokenisation Concept

Tokenisation replaces identifiable information with a generated reference.

Instead of:

email=user@example.com

Use:

?id=abc123xyz

The token maps internally to a user record,
but the URL itself contains no sensitive information.

---

# 3️⃣ Tokenisation Flow (Applied Model)

1. Employee list imported into simulation platform.
2. Platform generates unique token per user.
3. Tracking link embeds token.
4. When clicked, event stored against token.
5. Identity mapping occurs internally, not in URL.

Benefits:

- Reduced data exposure risk.
- Prevents identity leakage via link sharing.
- Simplifies anonymised reporting.

---

# 4️⃣ Data Minimisation Principle

Data minimisation means:

Collect only what is necessary to achieve the objective.

For phishing simulation:

Necessary:
- Click behaviour
- Timestamp
- Campaign reference

Not necessary:
- Raw passwords
- Full email body logging
- Device fingerprinting
- Excessive metadata

---

# 5️⃣ Design Comparison – Identity Handling

## Option 1 – Store Full User Identity with Event

Pros:
- Simple correlation
- Direct reporting

Cons:
- Higher privacy exposure
- Increased breach impact
- Compliance risk

Risk Level: Medium to High

---

## Option 2 – Token-Based Identity Mapping (Recommended)

Pros:
- Reduced exposure
- Easier anonymised analysis
- Controlled access to identity mapping

Cons:
- Requires secure mapping table
- Slightly more implementation complexity

Risk Level: Low

---

# 6️⃣ Credential Handling Policy

Critical ethical boundary:

Do not store real passwords.

If submission simulation exists:

- Capture only event occurrence.
- Mask input.
- Discard raw values immediately.

Storing real credentials introduces:

- Security liability
- Legal exposure
- Trust erosion

---

# 7️⃣ Data Retention Strategy

Retention must be defined:

Example model:

- Raw event logs retained short-term.
- Aggregated metrics retained longer.
- Identity mapping restricted and time-limited.

Long-term storage increases risk surface.

---

# 8️⃣ Access Control

Best practice:

- Role-based access to event data.
- Separate access for identity mapping.
- Audit logs enabled.
- Data export restricted.

Security team should not have unnecessary raw access.

---

# 9️⃣ Governance & Compliance Alignment

Tokenisation and data minimisation support:

- Privacy compliance principles.
- Ethical training frameworks.
- Internal policy alignment.
- Audit readiness.

Security awareness must not create privacy violations.

---

# 🔎 Interview Deep-Dive Hooks

Security Engineering:
- Why tokenisation reduces breach impact.

GRC:
- How data minimisation aligns with privacy frameworks.

SOC:
- Balancing observability and privacy.

Management:
- Why not naming individuals preserves trust.
