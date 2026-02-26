# Architecture Diagram – Internal Phishing Simulation (Defensive)

This document provides **visual architecture diagrams** for an authorised internal phishing simulation.
It focuses on **clarity**, **risk isolation**, and **governance controls**.

---

## 1) System Context Diagram (Components & Boundaries)

```mermaid
flowchart LR

subgraph User_Zone
    U["Employees<br/>Outlook + Browser<br/>Managed Devices"]
end

subgraph Enterprise_Email_Zone
    M["Microsoft Email Environment<br/>Exchange / Outlook<br/>Mail Filtering / Defender"]
end

subgraph Simulation_Platform_Zone
    P["Simulation Platform<br/>Campaign Config<br/>Tracking Links<br/>Event Logging"]
end

subgraph Hosting_Zone
    D["Simulation Domain + DNS"]
    W["Landing Page Hosting<br/>Isolated Cloud VM<br/>Web Server HTTPS"]
end

subgraph Reporting_Zone
    R["Reporting & Analysis<br/>Metrics + Segmentation<br/>Executive Summary"]
    G["Governance Controls<br/>Scope Approval<br/>Data Minimisation<br/>Retention Policy"]
end

U -->|Receives Email| M
M -->|Delivers Campaign| U
U -->|Clicks Link| D
D -->|Resolves to IP| W
W -->|Logs Event| P
P -->|Aggregated Data| R

G -.-> P
G -.-> W
G -.-> R
```
### How to explain this in interviews (30 seconds):

  - Users interact via Outlook and browser

  - Email flow is governed by Microsoft filtering controls

  - Domain/DNS routes users to an isolated landing page host

  - Platform logs events and feeds reporting

Governance overlays define scope, data boundaries, and retention
---
## 2) Control Points Diagram

This diagram shows where risks may occur and how they are mitigated.

```mermaid
flowchart TB

A[Campaign Setup<br/>Target List + Template + Schedule]
B[Email Delivery<br/>Mail Gateway / Filtering]
C[User Click<br/>DNS Resolution]
D[Landing Page Host<br/>Isolated Server]
E[Event Logging<br/>Platform Database]
F[Reporting<br/>Dashboards + Exec Summary]

A --> B --> C --> D --> E --> F

CP1{{Approval & Scope Control}}
CP2{{Delivery Validation}}
CP3{{DNS & Domain Reputation Monitoring}}
CP4{{Hosting Isolation & Monitoring}}
CP5{{Data Minimisation & Retention}}

CP1 -.-> A
CP2 -.-> B
CP3 -.-> C
CP4 -.-> D
CP5 -.-> E
CP5 -.-> F
```
#### What technical reviewers look for:

  - You know where risks occur (delivery blocked, DNS issues, host misconfig, over-collection)

  - You have controls (approval gates, test batches, isolation, monitoring, data limits)
---
## 3) End-to-End Sequence Diagram

```mermaid
sequenceDiagram

participant Emp as Employee (Browser)
participant DNS as DNS Resolver
participant Web as Landing Page Host
participant Sim as Simulation Platform
participant Rep as Reporting Layer

Emp->>DNS: Resolve simulation domain
DNS-->>Emp: Return hosting IP

Emp->>Web: GET landing page (tracking link)
Web->>Sim: Log click event (campaign ID + user token)
Sim-->>Web: Event stored confirmation

Web-->>Emp: Return landing page content

Sim->>Rep: Aggregate metrics
Rep-->>Sim: Reporting available
```
### Interview follow-up hooks:

  - What if DNS fails? (control point: DNS config & monitoring)

  - What if email is blocked? (control point: delivery validation / scoped whitelisting)

  - What data is stored? (control point: data minimisation / retention)

--
## 4) Defensive Design Principles

- Separate simulation domain from production domain.

- Isolate hosting environment from internal systems.

- Limit data collection to behavioural metrics.

- Ensure governance approval before launch.

- Notify SOC before campaign to avoid false escalation.

- Define decommission plan post-campaign.

--
## 5) Interview Talking Points

Infrastructure Focus:

- Why isolate hosting?

- What happens during DNS resolution?

Security Operations Focus:

- How to prevent false positive incident escalation?

Cloud Focus:

- How to scale hosting if campaign size increases?

Governance Focus:

- Where approval checkpoints exist in the workflow?

- How is data minimisation enforced?
