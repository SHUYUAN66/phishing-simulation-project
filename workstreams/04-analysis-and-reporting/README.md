# Workstream 04 – Analysis & Reporting

This workstream focuses on transforming simulation event data into actionable security insights.

It bridges technical logging and executive decision-making.

---

# 1️⃣ Executive Summary (Non-Technical)

The purpose of this workstream is to:

- Analyse behavioural data collected during the simulation.
- Identify risk patterns across the organisation.
- Provide clear, actionable reporting to management.
- Support targeted security awareness improvements.

This phase determines whether the campaign creates value.

---

# 2️⃣ Data Collection Overview

Typical event data includes:

- Campaign ID
- User reference (tokenised)
- Timestamp
- Event type (open / click / interaction)
- Department (if mapped during analysis)

No raw credentials stored.

---

# 3️⃣ Key Metrics

## A. Click Rate

Definition:
Percentage of users who clicked the tracking link.

Limitations:
Click rate alone does not represent true security posture.

---

## B. Repeat Behaviour

Track whether the same users click in multiple campaigns.

Purpose:
Identify persistent high-risk behaviour.

---

## C. Department Segmentation

Group results by function or department.

Purpose:
- Identify targeted awareness needs.
- Avoid organisation-wide generic training.

---

## D. Time-to-Click Analysis

Measure how quickly users interact after receiving email.

Purpose:
Understand reaction patterns.

---

# 4️⃣ Reporting Structure

## A. Technical Report (Security Team)

Includes:
- Raw metrics
- Event distribution
- Risk segmentation
- Trend analysis

---

## B. Executive Summary (Management)

Focus:
- High-level trends
- Risk areas
- Improvement recommendations
- Training alignment

Avoid:
- Individual shaming
- Excessive technical detail

---

# 5️⃣ Design Decisions & Trade-offs

## Decision 1 – Focus on Trends, Not Individuals

Reason:
- Encourage organisational improvement.
- Maintain trust.
- Align with awareness goals.

---

## Decision 2 – Behavioural Baseline First

Reason:
- First campaign establishes reference point.
- Improvement measured longitudinally.

---

## Decision 3 – Actionable Recommendations Required

Data without follow-up action reduces program value.

Examples:
- Targeted micro-training.
- Department workshops.
- Simulated follow-up testing.

---

# 6️⃣ Risk Considerations

## Risk: Overinterpretation of Data

Mitigation:
- Contextualise metrics.
- Avoid treating click rate as sole risk indicator.

---

## Risk: Data Privacy Exposure

Mitigation:
- Token-based identity handling.
- Limited access to raw logs.
- Defined retention policy.

---

## Risk: Trust Erosion

Mitigation:
- Share aggregated insights.
- Focus on learning outcomes.

---

# 7️⃣ Governance Controls

- Reporting access restricted.
- Data retention defined.
- Metrics reviewed by Security leadership.
- Follow-up actions documented.

---

# 8️⃣ Deliverables

- Campaign performance dashboard.
- Executive summary slide.
- Risk segmentation report.
- Improvement action plan.

---

# 9️⃣ Interview Deep-Dive Hooks

Security Operations:
- How to turn event logs into actionable detection insights.

Data / Analytics:
- Designing meaningful behavioural metrics.

GRC:
- Data minimisation and privacy boundaries.

Leadership:
- Communicating risk without creating fear.
