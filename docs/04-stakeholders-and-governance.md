# Stakeholders & Governance Model

This document defines the organisational structure, ownership model, and governance controls for the internal phishing simulation project.

The purpose is to demonstrate structured accountability and cross-team coordination.

---

# 1️⃣ Executive Overview

Phishing simulation is not only a technical exercise.  
It is an organisational activity requiring:

- Defined ownership
- Clear approval structure
- Risk control boundaries
- Communication alignment

Without governance, technical execution alone can create risk.

---

# 2️⃣ Key Stakeholder Groups

## A. Security Awareness / Information Security (Project Owner)

Role:
Primary owner of the phishing simulation program.

Responsibilities:
- Define campaign objectives
- Approve simulation scope
- Select target population
- Define acceptable metrics
- Ensure ethical boundaries
- Produce final risk report

Deliverables:
- Campaign design documentation
- Post-campaign executive report
- Improvement recommendations

---

## B. IT Infrastructure Team

Role:
Infrastructure and hosting control.

Responsibilities:
- Provision hosting environment
- Ensure server isolation
- Manage network-level configurations
- Maintain system uptime
- Support DNS configuration if required

Deliverables:
- Secure hosting environment
- Deployment documentation
- Decommission plan after campaign

---

## C. Domain & DNS Administrator

Role:
Domain lifecycle management.

Responsibilities:
- Register simulation domain
- Configure DNS records
- Ensure proper domain routing
- Monitor domain reputation

Deliverables:
- DNS configuration record
- Domain risk assessment
- Decommission timeline

---

## D. Microsoft Email / Exchange Administrator

Role:
Enterprise email flow management.

Responsibilities:
- Review mail flow configuration
- Test campaign delivery
- Adjust filtering rules if required
- Prevent unnecessary security escalations

Deliverables:
- Mail delivery validation report
- Temporary rule documentation (if applied)

---

## E. Security Operations Center (SOC)

Role:
Monitoring and incident coordination.

Responsibilities:
- Be informed prior to campaign launch
- Prevent false incident escalation
- Monitor abnormal behaviour during campaign
- Validate that campaign activity remains within scope

Deliverables:
- Monitoring acknowledgment
- Incident handling protocol confirmation

---

## F. HR / Internal Communications

Role:
Employee communication alignment.

Responsibilities:
- Align messaging tone
- Ensure training framing
- Support post-campaign awareness messaging
- Protect organisational trust

Deliverables:
- Communication draft review
- Awareness follow-up materials

---

## G. Legal / Compliance (If Required)

Role:
Regulatory oversight.

Responsibilities:
- Review data collection boundaries
- Ensure privacy compliance
- Validate policy alignment

Deliverables:
- Formal approval (if required by organisation size)

---

# 3️⃣ Governance Model

## Approval Flow

1. Campaign proposal drafted (Security team)
2. Risk assessment completed
3. Stakeholder review (IT, Email, SOC)
4. Governance approval (Management / Legal if required)
5. Controlled launch
6. Reporting & review
7. Decommission infrastructure

---

# 4️⃣ RACI Model (Responsibility Matrix)

| Function | Security | IT | Email Admin | SOC | HR | Legal |
|----------|----------|----|-------------|-----|----|-------|
| Scope Definition | R | C | C | C | C | C |
| Hosting Setup | C | R | - | - | - | - |
| Email Delivery | C | C | R | C | - | - |
| Monitoring | C | C | C | R | - | - |
| Risk Approval | A | C | C | C | C | A |
| Reporting | R | - | - | C | C | C |

Legend:
- R = Responsible
- A = Accountable
- C = Consulted

---

# 5️⃣ Governance Principles

- Least privilege access
- Data minimisation
- Documented approval trail
- Clear communication plan
- Infrastructure isolation
- Defined decommission plan

---

# 6️⃣ Organisational Maturity Indicators

A mature phishing simulation program demonstrates:

- Executive sponsorship
- Cross-team coordination
- Clear ethical boundaries
- Documented risk mitigation
- Measurable improvement over time

---

# 7️⃣ Interview Focus Areas

SOC Focus:
- Cross-team incident coordination

Infrastructure Focus:
- Separation of duties

GRC Focus:
- Governance model & approval flow

Management Focus:
- Stakeholder communication and trust protection
