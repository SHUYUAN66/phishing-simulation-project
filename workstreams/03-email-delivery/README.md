# Workstream 03 – Email Delivery (Microsoft Enterprise Environment)

This workstream covers the controlled delivery of simulation emails within a Microsoft enterprise mail environment.

It focuses on mail flow validation, filtering alignment, and operational safety.

---

# 1️⃣ Executive Summary (Non-Technical)

This component ensures that:

- Simulation emails are delivered to authorised employees.
- Email delivery does not disrupt business operations.
- Security systems do not trigger unnecessary escalation.
- The campaign remains controlled and scoped.

This is not about bypassing security.
It is about coordinating with enterprise controls responsibly.

---

# 2️⃣ Technical Responsibilities

## A. Mail Flow Understanding

Typical enterprise mail flow:

Simulation Platform  
→ SMTP  
→ Microsoft Exchange / Email Gateway  
→ Filtering (Defender / Anti-spam rules)  
→ Employee Inbox

Each stage may block or modify email delivery.

---

## B. Pre-Campaign Validation

Before full rollout:

- Send test batch to controlled accounts.
- Validate inbox delivery.
- Confirm no unintended spam/quarantine behaviour.
- Verify tracking links function correctly.

---

## C. Authentication Considerations

Depending on configuration:

- SPF records (sender validation)
- DKIM signing (message integrity)
- DMARC alignment (policy enforcement)

These increase delivery reliability and reduce rejection risk.

---

## D. Coordination with Email Admin

Enterprise email administrators may:

- Temporarily adjust filtering thresholds.
- Scope whitelisting for simulation domain.
- Monitor unusual mail flow spikes.

All changes must be documented and reversible.

---

# 3️⃣ Design Decisions & Trade-offs

## Decision 1 – Coordinate Rather Than Bypass

Reason:
- Avoid undermining security controls.
- Maintain trust with infrastructure teams.
- Ensure simulation remains ethical and auditable.

Trade-off:
- May reduce realism slightly.

---

## Decision 2 – Controlled Campaign Waves

Reason:
- Prevent mail flood detection.
- Avoid overwhelming mail systems.
- Reduce reputation impact.

Alternative:
- Send to entire organisation at once.

Risk:
- Trigger spam thresholds.

---

## Decision 3 – Avoid Triggering SOC Escalation

Reason:
- Prevent unnecessary incident response.
- Avoid operational disruption.

Mitigation:
- Pre-notification to SOC.
- Clearly scoped simulation identifiers.

---

# 4️⃣ Risk Considerations

## Risk: Email Blocked by Filtering

Mitigation:
- Test campaign.
- Validate authentication records.
- Align with email administrator.

---

## Risk: Mail Reputation Impact

Mitigation:
- Controlled volume.
- Short campaign duration.
- Separate simulation domain.

---

## Risk: SOC False Positive

Mitigation:
- Advance notification.
- Campaign metadata logging.
- Controlled scope communication.

---

# 5️⃣ Governance Controls

- Campaign approved before sending.
- Target list validated.
- Email administrator informed.
- SOC coordination completed.
- Rollback plan defined.

---

# 6️⃣ Deliverables

- Mail flow validation report.
- Test campaign results.
- Authentication configuration documentation.
- Post-campaign delivery metrics.

---

# 7️⃣ Interview Deep-Dive Hooks

Infrastructure Focus:
- Explain Microsoft mail flow stages.

Security Operations Focus:
- How to avoid triggering detection systems.

Cloud Focus:
- Handling large-scale campaign delivery.

GRC Focus:
- Why coordination is critical before sending.
