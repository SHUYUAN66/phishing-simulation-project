# Internal Phishing Simulation – Defensive Security Project

This repository documents an **authorised internal phishing simulation** used for **security awareness training** and **risk reduction**.

It is written to be:
- **Readable for non-technical stakeholders** (purpose, scope, governance)
- **Credible for technical reviewers** (architecture, controls, operational flow)
- **Useful for interviews** (design reasoning, trade-offs, follow-up questions)

⚠️ Defensive use only. No unauthorised activity.

---

## Quick Start (Where to begin)

1) **Project context** → `docs/01-project-context.md`  
2) **Architecture diagrams** → `docs/architecture-diagram.md`  
3) **Risks & ethics** → `docs/03-risk-considerations.md`  
4) **Stakeholders & governance** → `docs/04-stakeholders-and-governance.md`  
5) **Workstreams (by department)** → `workstreams/`  
6) **Interview deep-dive** → `interview-prep/possible-follow-up-questions.md`

---

## Repository Map

### 1) Background Knowledge (for beginners)
Explains foundations required to understand the project.
- Networking → `background/01-networking-foundations.md`
- DNS & Domain → `background/02-dns-and-domain-model.md`
- Email & SMTP → `background/03-email-flow-and-smtp.md`
- Web App Basics → `background/04-web-application-model.md`
- Cloud Hosting → `background/05-cloud-hosting-model.md`

### 2) Project Documentation (business + architecture)
- Project context (why / audience / scope / success metrics) → `docs/01-project-context.md`
- System architecture overview → `docs/02-system-architecture.md`
- Architecture diagrams (visual) → `docs/architecture-diagram.md`
- Risk & ethical considerations → `docs/03-risk-considerations.md`
- Stakeholders & governance (RACI + approvals) → `docs/04-stakeholders-and-governance.md`

### 3) Workstreams (departments / parties)
Each folder describes responsibilities, inputs/outputs, process, and controls.
- Domain & DNS → `workstreams/01-domain-dns/`
- Web & Simulation Platform Integration → `workstreams/02-web-gophish/`
- Email Delivery (Microsoft Environment) → `workstreams/03-email-delivery/`
- Analysis & Reporting → `workstreams/04-analysis-and-reporting/`

### 4) Interview Preparation
- Follow-up questions and structured answer thinking → `interview-prep/possible-follow-up-questions.md`

### 5) Assets
- Diagrams and images → `assets/images/`

---

## What this project demonstrates (skill highlights)

### Security Operations / SOC
- Behavioural metrics (open/click trends), segmentation, reporting workflows
- Coordination to avoid false incident escalation

### Infrastructure / Cloud
- Isolation design, hosting lifecycle, DNS routing model
- Operational considerations for scale and reliability

### GRC (Governance, Risk, Compliance)
- Ethical boundaries, data minimisation, approval workflows
- Stakeholder alignment and communication controls

### Red/Blue Understanding (Defensive perspective)
- Realism vs safety boundaries
- How controls constrain simulation design

---

## Safety Disclaimer
This repository describes **defensive security awareness operations** only.
Any simulation must be authorised, scoped, and compliant with organisational policies.
