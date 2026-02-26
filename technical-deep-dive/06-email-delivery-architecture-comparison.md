# Technical Deep Dive 02 – Email Delivery Architecture & Design Comparison

This document explores enterprise email delivery architecture
and the technical considerations behind simulation campaign delivery.

The goal is to demonstrate applied understanding of SMTP,
email authentication mechanisms, and filtering systems.

---

# 1️⃣ Enterprise Email Architecture (High-Level)

Typical enterprise email flow:

Sender (Simulation Platform)
→ SMTP Server
→ Public Internet
→ Receiving Mail Gateway
→ Filtering Layer (Spam / Defender)
→ Mailbox (Exchange / Outlook)

Each stage introduces validation and risk controls.

Email delivery reliability depends on:

- Proper SMTP configuration
- Domain authentication records
- Sender reputation
- Filtering alignment

---

# 2️⃣ SMTP Flow (Simplified Technical View)

SMTP operates over TCP (typically port 25 or 587).

Basic flow:

1. Client connects to mail server.
2. HELO / EHLO handshake.
3. MAIL FROM command.
4. RCPT TO command.
5. DATA transmission.
6. Server response (accept / reject).

SMTP does not encrypt by default.
Encryption may be added via STARTTLS.

Key insight:
SMTP defines message transfer, not trust validation.

---

# 3️⃣ Email Authentication Mechanisms

Email authentication protects against spoofing.

---

## A. SPF (Sender Policy Framework)

SPF record (DNS TXT record) defines:

Which servers are allowed to send mail on behalf of a domain.

Receiving server checks:
- Sending IP matches SPF record.

Limitation:
SPF alone does not guarantee message integrity.

---

## B. DKIM (DomainKeys Identified Mail)

DKIM:
- Cryptographically signs email headers.
- Receiving server validates signature using public key in DNS.

Provides:
- Integrity verification.
- Domain-level authentication.

---

## C. DMARC (Domain-based Message Authentication, Reporting & Conformance)

DMARC:
- Builds on SPF & DKIM.
- Defines policy (none / quarantine / reject).
- Provides reporting mechanism.

DMARC ensures alignment between:
- Visible "From" domain
- Authenticated sending domain

---

# 4️⃣ Why Emails Get Blocked

Enterprise filters evaluate:

- Sender reputation.
- Domain age.
- IP reputation.
- Volume anomalies.
- Content similarity patterns.
- Authentication failure (SPF/DKIM/DMARC).

Common blocking causes:

- Missing SPF record.
- DKIM signature invalid.
- DMARC policy misaligned.
- High-volume sudden sending.
- Suspicious link patterns.

---

# 5️⃣ Design Comparison – Delivery Strategies

## Option 1 – Direct SMTP from Hosting Server

Pros:
- Full control.
- Simpler architecture.

Cons:
- Higher reputation risk.
- Harder IP warm-up.
- More likely to trigger spam filters.

---

## Option 2 – Dedicated Mail Relay Service

Pros:
- Managed reputation.
- Better delivery reliability.
- Built-in authentication tools.

Cons:
- Additional cost.
- Less infrastructure control.

---

## Option 3 – Internal Mail Relay (Enterprise Approved)

Pros:
- Trusted internal route.
- Lower external reputation risk.

Cons:
- Requires heavy coordination.
- May reduce realism.

---

# 6️⃣ Applied Trade-Off in Simulation Context

In controlled enterprise simulations:

- Delivery must align with policy.
- Reputation damage must be avoided.
- Security controls must not be undermined.

Preferred approach:
Coordinated delivery with email administrators,
using authenticated domain and controlled campaign waves.

Not bypassing security, but operating within governance.

---

# 7️⃣ Campaign Wave Strategy

Sending entire organisation at once increases:

- Spam detection risk.
- Reputation impact.
- SOC alert likelihood.

Wave-based sending:

- Smaller batches.
- Time-distributed.
- Monitoring between waves.

This reduces systemic impact.

---

# 8️⃣ Risk & Governance Considerations

- Pre-campaign validation testing.
- Authentication records verified.
- SOC pre-notified.
- Rollback plan prepared.
- Post-campaign review conducted.

---

# 9️⃣ Engineering Reflection

Email delivery is not just protocol-based.
It is reputation-based and behaviour-based.

Reliable simulation delivery requires:

- Authentication correctness.
- Reputation awareness.
- Volume control.
- Governance coordination.

Security engineering involves working with controls,
not bypassing them.

---

# 🔎 Interview Deep-Dive Hooks

Infrastructure:
- Explain SPF/DKIM/DMARC interaction.

Security:
- Why reputation impacts mail acceptance.

Cloud:
- Compare self-hosted SMTP vs relay service.

GRC:
- Why delivery strategy must align with policy.
