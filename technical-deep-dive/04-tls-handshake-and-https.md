# Technical Deep Dive 04 – TLS Handshake & HTTPS

This document explains TLS and HTTPS from an applied security perspective.

---

# 1️⃣ Why HTTPS Is Required

Landing pages must use HTTPS to:
- Avoid browser warnings
- Protect integrity
- Prevent interception
- Maintain user trust

HTTPS = HTTP over TLS.

---

# 2️⃣ TLS Handshake (Simplified Flow)

1. Client Hello (supported cipher suites)
2. Server Hello (chosen cipher suite)
3. Server sends certificate
4. Client verifies certificate
5. Key exchange
6. Encrypted communication begins

---

# 3️⃣ Certificate Validation

Client checks:
- Certificate authority trust chain
- Expiry date
- Domain match
- Revocation status

If validation fails:
Browser displays warning.

---

# 4️⃣ Security Properties

TLS provides:
- Confidentiality (encryption)
- Integrity (tamper detection)
- Authentication (server identity)

---

# 5️⃣ Applied Design Insight

Using valid TLS certificates:
- Prevents suspicion
- Ensures compatibility
- Reduces user confusion
- Supports ethical transparency

TLS is a reliability and trust requirement.
