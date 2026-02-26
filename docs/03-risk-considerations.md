# Risk & Ethical Considerations – Internal Phishing Simulation

This document outlines the risk landscape, governance considerations, and ethical boundaries associated with conducting an internal phishing simulation.

The purpose is to demonstrate risk-aware security engineering.

---

# 1️⃣ Executive Summary (Non-Technical View)

Phishing simulations are security awareness tools, but they introduce operational and reputational risks if not properly governed.

Key risk domains:

- Reputational risk
- Employee trust impact
- Technical infrastructure risk
- Legal and compliance exposure
- Data handling and privacy concerns

Proper governance and scope control are essential.

---

# 2️⃣ Risk Categories

## A. Reputational Risk

Risk:
- Employees feel deceived.
- Simulation leaks externally.
- Domain flagged publicly as malicious.

Mitigation:
- Executive sponsorship.
- Clearly documented internal policy.
- Transparent post-campaign communication.
- Separate simulation domain.

---

## B. Technical Infrastructure Risk

Risk:
- Domain blacklisting.
- Email delivery blocked.
- Hosting server misconfigured.
- Overload if high click volume.

Mitigation:
- Controlled DNS configuration.
- Pre-campaign test batch.
- Isolated hosting environment.
- Monitoring during campaign.

---

## C. Security Detection Risk

Risk:
- SOC treats simulation as real attack.
- Incident response escalation triggered.

Mitigation:
- Pre-coordination with SOC.
- Temporary rule adjustments if required.
- Clear internal notification to security team.

---

## D. Data & Privacy Risk

Risk:
- Collecting real passwords.
- Storing unnecessary personal data.
- Violating internal privacy policy.

Mitigation:
- Data minimisation principle.
- Avoid storing raw credentials.
- Limit data retention period.
- Approved data access controls.

---

## E. Organisational Trust Risk

Risk:
- Employees lose trust in IT/security.
- Negative morale impact.

Mitigation:
- Educational framing (training focus).
- Avoid overly aggressive simulation tactics.
- Share improvement insights, not shame metrics.

---

# 3️⃣ Ethical Boundaries

This simulation must:

- Be formally authorised.
- Stay within approved internal scope.
- Avoid collecting real credentials.
- Avoid harming production systems.
- Avoid deception that causes panic or operational disruption.

Security awareness must never become security harm.

---

# 4️⃣ Governance Model

Recommended governance structure:

- Project Owner: Security Awareness / InfoSec
- Technical Owner: Infrastructure / Email Admin
- Risk Approval: Security Management / Legal (if required)
- HR / Communications: Awareness alignment

All activities documented and approved before execution.

---

# 5️⃣ Compliance Considerations

Depending on jurisdiction:

- Employee privacy law
- Data retention requirements
- Acceptable use policies
- Internal audit review

Phishing simulation must align with corporate governance frameworks.

---

# 6️⃣ Lessons Learned (Risk Perspective)

Key reflections:

- Technical realism must be balanced with organisational stability.
- Security operations must coordinate closely with governance.
- Awareness campaigns require stakeholder management as much as infrastructure design.
- Risk modelling should occur before technical deployment.

---

# 7️⃣ Interview Highlight Areas

Security Operations:
- Incident coordination control.

Infrastructure:
- Domain and hosting risk isolation.

GRC:
- Data minimisation and ethical boundary enforcement.

Management Track:
- Stakeholder communication planning.
