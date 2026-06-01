# Vulcan Insight

## Executive Summary

Vulcan Works faces increasing operational challenges caused by fragmented data, disconnected systems, manual reporting processes, and a strong dependency on individual employees for critical information retrieval.

Production, quality, and operational data exist across multiple systems that do not communicate effectively. As a result, root cause investigations are slow, quality issues are identified too late, reporting requires significant manual effort, and valuable operational knowledge remains locked within a small number of experts.

Vulcan Insight addresses these challenges by creating a centralized data and knowledge platform that combines operational data from multiple systems into a single trusted source of information.

The platform uses traditional software for data integration, storage, security, reporting, and KPI calculations, while AI is applied only where it creates measurable business value through knowledge retrieval, investigation support, and report generation.

---

# Business Problems

## Production

* Defects and quality issues are detected too late.
* Rework costs continue to increase.
* Downtime investigations are slow and difficult.

## Operations

* Critical knowledge depends on a few key individuals.
* Data retrieval is manual and time consuming.
* Information is scattered across multiple systems.

## Compliance

* Audit preparation requires significant effort.
* ISO reporting is largely manual.
* Consistent evidence for improvements is difficult to provide.

---

# Solution Architecture

## High Level Overview

```text
SAP
MES
QMS
Machine Data
Maintenance Systems
Operational Databases
        │
        ▼
┌───────────────────────┐
│ Unified Data Layer    │
│ Single Source of Truth│
└───────────────────────┘
        │
        ▼
┌───────────────────────┐
│ Security Layer        │
│ Access Control        │
│ NDA Protection        │
│ Data Minimization     │
└───────────────────────┘
        │
        ▼
┌───────────────────────┐
│ Query & Analytics     │
│ KPI Engine            │
│ Data Aggregation      │
└───────────────────────┘
        │
        ▼
┌───────────────────────┐
│ AI Agent Layer        │
└───────────────────────┘
        │
 ┌──────┼──────┐
 ▼      ▼      ▼
Knowledge  Investigation  Reporting
 Agent        Agent         Agent
        │
        ▼
Users / Dashboards / Reports
```

---

# Data Flow

The AI never receives unrestricted raw production data.

Instead, the platform first performs:

* Access validation
* NDA verification
* Data filtering
* KPI calculations
* Data aggregation
* Context preparation

Only the resulting business context is provided to the AI.

Example:

User Question:

"Why did rework increase on Line 3 last week?"

System Process:

```text
User Question
        │
        ▼
Permission Check
        │
        ▼
Relevant Data Selection
        │
        ▼
KPI Calculation
        │
        ▼
Context Package
        │
        ▼
LLM Analysis
        │
        ▼
Human Review
        │
        ▼
Final Decision
```

Example Context Sent to AI:

* Rework increased from 3.2% to 7.4%
* Torque station alarms increased by 38%
* Maintenance intervention occurred Tuesday
* Similar event recorded in March

The AI receives only this filtered context, not complete production databases or customer information.

---

# AI Components

## Knowledge Agent

Purpose:

Provide fast access to operational and technical knowledge.

Examples:

* Which system contains downtime data?
* How is OEE calculated?
* What information is required for ISO reporting?

Business Value:

* Reduced dependency on experts
* Faster onboarding
* Better knowledge retention

---

## Investigation Agent

Purpose:

Support root cause investigations.

Examples:

* Why did rework increase?
* Why did downtime occur?
* Have similar incidents happened before?

Business Value:

* Faster investigations
* Better operational decisions
* Improved transparency

---

## Reporting Agent

Purpose:

Automate report preparation.

Examples:

* ISO 9001 reports
* Quality reports
* Management summaries
* Audit preparation packages

Business Value:

* Reduced reporting effort
* Faster audits
* More consistent documentation

---

# GDPR Strategy

The platform primarily processes machine and operational data.

Limited personal data may include:

* User accounts
* Employee names
* Shift information
* Maintenance records

Controls:

* Role based access control
* Encryption
* Audit logging
* Pseudonymization where appropriate
* Data minimization

Lawful Basis:

Legitimate Interest under Article 6(1)(f) GDPR.

---

# NDA and Intellectual Property Protection

Vulcan Works operates under customer NDAs and OEM agreements.

Protection Measures:

* On premises deployment
* No unrestricted external data transfer
* Document classification
* Role based permissions
* Restricted customer data access
* Audit trail for all AI requests

The AI can only access information that the requesting user is authorized to view.

---

# EU AI Act Classification

Risk Level:

Minimal Risk

Justification:

* No automated decisions
* No machine control
* No employee evaluation
* No safety critical operation
* Human approval required

Role Allocation:

SilverTrust = Provider

Vulcan Works = Deployer

---

# LangSmith Monitoring

LangSmith is used to monitor the AI system, not the production systems.

Tracked Information:

* User requests
* Retrieved documents
* Generated responses
* Investigation outputs
* Report generation
* Latency
* Errors
* User feedback

Benefits:

* Full transparency
* AI auditability
* Trust in AI generated insights
* Evidence for compliance reviews

Every AI generated report, recommendation, and investigation can be traced back to its source and reviewed by authorized personnel.
