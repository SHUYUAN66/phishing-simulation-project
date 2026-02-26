# Internal Phishing Simulation – Defensive Security Engineering Project

This repository documents the technical and organisational design of an internal phishing simulation conducted for security awareness purposes.

The documentation is structured to support:

- Executive understanding (non-technical stakeholders)
- Technical validation (engineers & security professionals)
- Interview deep-dive discussions (design reasoning & trade-offs)

⚠️ This project describes an authorised, defensive security awareness exercise only.

---

# 📌 How to Read This Repository

This repository is structured in layered depth:

## Level 1 – Business & Governance Context
- Project Context → `docs/01-project-context.md`
- Stakeholders & Governance → `docs/04-stakeholders-and-governance.md`
- Risk & Ethical Considerations → `docs/03-risk-considerations.md`

## Level 2 – Technical Architecture
- System Architecture Overview → `docs/02-system-architecture.md`

## Level 3 – Technical Foundations
- Networking Foundations → `background/01-networking-foundations.md`
- DNS & Domain Model → `background/02-dns-and-domain-model.md`
- Email & SMTP Flow → `background/03-email-flow-and-smtp.md`
- Web Application Model → `background/04-web-application-model.md`
- Cloud Hosting Model → `background/05-cloud-hosting-model.md`

## Level 4 – Operational Workstreams
- Domain & DNS Management → `workstreams/01-domain-dns/`
- Web & GoPhish Integration → `workstreams/02-web-gophish/`
- Email Delivery & Microsoft Controls → `workstreams/03-email-delivery/`
- Reporting & Security Analysis → `workstreams/04-analysis-and-reporting/`

## Interview Preparation
- Possible Technical Deep-Dive Questions → `interview-prep/possible-follow-up-questions.md`

---

# 🎯 Engineering Focus Areas

This project highlights:

- Enterprise email flow understanding
- Infrastructure-level reasoning (DNS, SMTP, hosting)
- Cross-team coordination in security exercises
- Risk management & ethical control boundaries
- Data-driven security reporting

---

# Design Philosophy

Every section includes:
- Executive Summary
- Technical Explanation
- Design Considerations & Trade-offs

This allows both non-technical and technical readers to follow the material appropriately.
