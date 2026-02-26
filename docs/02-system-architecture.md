# System Architecture – Internal Phishing Simulation

This document explains the high-level technical architecture of the phishing simulation system.

The explanation is structured in three layers:
1. Executive Summary
2. Technical Flow
3. Design Decisions & Trade-offs

---

# 1️⃣ Executive Summary (Non-Technical View)

The phishing simulation system consists of five major components:

1. Target Users (Employees)
2. Email Delivery System (Microsoft Environment)
3. Phishing Simulation Platform (e.g., GoPhish)
4. Web Hosting Server (Landing Page)
5. Reporting & Analysis Layer

High-level flow:

User → Email → Click Link → Landing Page → Event Recorded → Security Reporting

The system is controlled, authorised, and limited to internal training purposes only.

---

# 2️⃣ Technical Architecture Overview

## Core Components

### 1. Employee Endpoint
- Outlook client
- Browser
- Corporate device or managed endpoint

### 2. Email Delivery Layer
- SMTP protocol
- Microsoft Exchange / Outlook mail flow
- Security filtering (Defender / mail gateway rules)

### 3. Phishing Simulation Platform
- Campaign configuration
- Email template management
- Unique tracking link generation
- Event logging (open, click, submission if applicable)

### 4. Web Hosting Layer
- Cloud-hosted server (e.g., Linux VM)
- HTTP/HTTPS web server
- Landing page (HTML / JavaScript)
- Tracking redirection logic

### 5. Data & Reporting Layer
- Event database
- Metrics aggregation
- Risk segmentation analysis
- Executive summary reporting

---

# 3️⃣ End-to-End Flow (Detailed)

## Step 1 – Campaign Setup
- Import approved employee list
- Generate unique tracking URLs
- Configure sender profile and SMTP settings

## Step 2 – Email Delivery
GoPhish → SMTP → Microsoft mail server → Inbox

Potential control points:
- Spam filtering
- Domain reputation
- Sender authentication (SPF/DKIM/DMARC)

## Step 3 – User Interaction
User opens email → clicks link

Browser resolves:
Domain → DNS → Server IP → Web page

## Step 4 – Event Logging
- Click event recorded
- Optional submission event recorded
- Timestamp + campaign ID + user ID stored

## Step 5 – Reporting & Analysis
Security team analyses:
- Click rate
- Department breakdown
- Repeat click behaviour
- Trend over time

---

# 4️⃣ Design Decisions & Trade-offs

## Decision 1 – Use Dedicated Simulation Domain

Reason:
- Realistic scenario
- Controlled environment
- Avoid interfering with production domain reputation

Alternative:
- Subdomain of corporate domain

Risk:
- Corporate reputation impact

Mitigation:
- Use clearly scoped and authorised domain.

---

## Decision 2 – Separate Hosting from Email System

Reason:
- Clear separation of responsibilities
- Easier infrastructure control
- Reduced blast radius

Trade-off:
- More configuration complexity

---

## Decision 3 – Limit Data Collection

Reason:
- Ethical boundaries
- Compliance requirements
- Avoid storing real credentials

Risk:
- Over-collection of sensitive data

Mitigation:
- Log behaviour only (click / interaction), not real passwords.

---

# 5️⃣ Risk & Control Considerations

Potential Risks:

- Email blocked by security gateway
- Domain flagged as malicious
- Employees misunderstand simulation
- Trust damage if poorly communicated

Controls:

- Pre-approved scope
- Internal communication strategy
- Whitelisting where required
- Post-campaign transparency

---

# 6️⃣ Scalability Considerations

If scaling to larger enterprise:

- Load balancing for web hosting
- Dedicated reporting pipeline
- SIEM integration
- Automated segmentation by department
- Integration with LMS (training system)

---

# 🔎 Interview Focus Highlights

### Security Operations Focus
- Event logging and behavioural metrics
- Risk-based segmentation

### Infrastructure / Cloud Focus
- DNS resolution path
- Hosting isolation model
- Mail flow controls

### Governance / Risk Focus
- Ethical scope definition
- Data minimisation
- Stakeholder communication

### Red/Blue Understanding Focus
- Realistic simulation design
- Detection evasion vs ethical limits
