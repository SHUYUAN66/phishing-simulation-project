# Workstream 02 – Web & Simulation Platform Integration

This workstream covers the configuration of the phishing simulation platform
and the integration between tracking logic and the hosted landing page.

The focus is controlled event logging, isolation, and ethical boundaries.

---

# 1️⃣ Executive Summary (Non-Technical)

This component is responsible for:

- Configuring the phishing simulation campaign.
- Generating unique tracking links.
- Hosting a controlled landing page.
- Logging behavioural events (e.g., click activity).

It does NOT perform malicious exploitation.
It is designed purely for awareness measurement.

---

# 2️⃣ Technical Responsibilities

## A. Campaign Configuration

The simulation platform is used to:

- Import authorised employee list.
- Create email template.
- Generate unique tracking URLs.
- Schedule controlled campaign waves.

Each recipient receives a unique tokenised link.

---

## B. Tracking Link Logic

Tracking link structure:

https://simulation-domain.com/?id=unique_token

The unique token allows:

- Mapping click event to campaign.
- Identifying user behaviour (within approved scope).
- Aggregating metrics without exposing sensitive data.

---

## C. Landing Page Hosting

Landing page hosted on isolated server.

Responsibilities:

- Serve HTML page.
- Trigger event logging when accessed.
- Avoid storing real credentials.
- Ensure HTTPS encryption.

Hosting environment separated from production systems.

---

## D. Event Logging

When user clicks:

1. Web server receives request.
2. Tracking token validated.
3. Click event recorded in simulation platform database.
4. Optional submission event recorded (if within scope).

Stored data typically includes:

- Campaign ID
- Token / user reference
- Timestamp
- Event type (click/open/submission if applicable)

---

# 3️⃣ Design Decisions & Trade-offs

## Decision 1 – Token-Based Tracking

Reason:
- Avoid embedding sensitive data in URL.
- Enable scalable event aggregation.
- Maintain separation between identity and behaviour.

Trade-off:
- Requires secure token generation and validation.

---

## Decision 2 – Isolated Hosting Environment

Reason:
- Reduce blast radius.
- Prevent lateral risk to corporate infrastructure.
- Easier shutdown post-campaign.

Alternative:
- Host within corporate web infrastructure.

Risk:
- Production system exposure.

---

## Decision 3 – Data Minimisation

Reason:
- Ethical boundaries.
- Compliance alignment.
- Reduce risk of sensitive data retention.

Implementation:
- Avoid storing raw credentials.
- Store behavioural metadata only.
- Define retention period.

---

# 4️⃣ Risk Considerations

## Risk: Excessive Data Collection

Mitigation:
- Log behavioural events only.
- Mask or discard any unintended sensitive input.
- Restrict database access.

---

## Risk: Hosting Misconfiguration

Mitigation:
- Pre-launch validation.
- HTTPS enforced.
- Logging monitored.
- Post-campaign decommission.

---

## Risk: Platform Misuse

Mitigation:
- Access restricted to authorised security personnel.
- Change logs documented.
- Campaign scope approval required.

---

# 5️⃣ Governance Controls

- Campaign scope approved before configuration.
- Target list validated.
- Platform access limited by role.
- Data retention timeline defined.
- Decommission procedure documented.

---

# 6️⃣ Deliverables

- Campaign configuration record.
- Email template archive.
- Tracking logic documentation.
- Event logging validation report.
- Post-campaign data export.

---

# 7️⃣ Interview Deep-Dive Hooks

Security Engineering:
- How tokenisation prevents sensitive data exposure.
- How event logging pipeline works.

Cloud / Infrastructure:
- Why isolate hosting from production network.
- How to scale landing page under high traffic.

SOC:
- How to prevent triggering detection rules.

GRC:
- Why credential storage is restricted.
- How long behavioural data should be retained.
