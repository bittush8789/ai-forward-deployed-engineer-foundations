# AI Forward Deployed Engineer (AI FDE) Fundamentals: Problem Framing



This document serves as the comprehensive master reference manual for **Phase 4: Problem Framing**, taking you from beginner concepts to enterprise-grade execution in problem definition, root cause diagnosis, use case prioritization, journey mapping, future state design, risk mapping, and constraint modeling.

---

# Phase 4: Problem Framing

---

## Module 1: Problem Identification

### 1. Detailed Theory & Taxonomy
Problem Framing is the foundational practice of defining the boundaries, root causes, constraints, and business significance of an operational challenge. An FDE must look past immediate symptoms (e.g., "The call queue is too long") to define the true structural problem (e.g., "Agents spend 70% of call time manually searching for policy exceptions across fragmented document silos").

```
  SYMPTOM: "Users complain the tool is slow" (Surface symptom)
     └── DIRECT CAUSE: API database requests take 8 seconds (Technical cause)
          └── ROOT PROBLEM: Missing index and poor SQL query structures (Systemic problem)
```

---

### 2. Enterprise Framework: The Problem Statement Canvas
FDEs use this canvas to structure initial scoping discussions:
```
+---------------------------------------------------------------------------------------+
| 1. What is the business problem?                                                      |
| [Describe the operational friction and its direct business cost]                      |
+---------------------------------------+-----------------------------------------------+
| 2. Who is affected?                   | 3. What systems/data are involved?            |
| [Define user personas and stakeholders] | [List databases, legacy apps, paper inputs]   |
+---------------------------------------+-----------------------------------------------+
| 4. What is the success metric?                                                        |
| [Define quantifiable target, e.g., 40% speedup, 0% compliance issues]                 |
+---------------------------------------------------------------------------------------+
```

---

### 3. Checklists & Templates
#### Discovery Question Bank
- [ ] What is the direct financial cost of the current process delay (e.g., SLAs missed, headcount required)?
- [ ] What is the manual process step that operators complain about the most?
- [ ] Where is the data generated, and is it accessible to outside services?
- [ ] How does the organization handle exceptions when the standard process fails?

---

## Module 2: Root Cause Analysis (RCA)

### 1. Detailed Theory & Methodologies
Root Cause Analysis (RCA) is the systematic process of identifying the underlying drivers of a process failure or efficiency bottleneck.

#### RCA Frameworks:
*   **5 Whys:** Peeling away symptoms by asking "Why" multiple times until a structural cause is revealed.
*   **Fishbone (Ishikawa) Diagram:** Categorizing potential causes under People (training issues), Process (workflow gaps), Technology (system latency), and Data (poor document scans).
*   **Fault Tree Analysis:** A top-down approach mapping the logical paths that lead to a system-level failure.

---

### 2. Enterprise Framework: The Fishbone Diagnosis Tool
```
     PEOPLE                      PROCESS
  Lack of training ──┐        ┌── Stale procedures
                     │        │
                     ├───► SYSTEM FAILS ◄───┤
                     │                      │
  Old legacy apps ───┘        └── Low OCR quality
     TECHNOLOGY                    DATA
```

---

### 3. Checklists & Templates
#### Root Cause Investigation Template
```markdown
# Root Cause Analysis: [Incident/Problem Name]

## 1. Problem Definition
*   **Observed Failure:** [e.g., 20% of auto-matching transactions fail]
*   **Identified Impact:** $[Amount] in manual reprocessing costs monthly.

## 2. Root Cause Mapping (5 Whys)
1. Why did the match fail? -> The invoice metadata did not match the PO.
2. Why didn't it match? -> The invoice date formats were parsed incorrectly.
3. Why were they parsed incorrectly? -> The OCR failed on low-resolution scans.
4. Why were scans low-resolution? -> The branch scanners are set to low-dpi mode to save bandwidth.
5. Why are scanners in low-dpi mode? -> There is no central device configuration policy.
```

---

## Module 3: Use Case Discovery & Prioritization

### 1. Detailed Theory
Use Case Discovery is the practice of cataloging and filtering potential AI opportunities to focus resources on the projects that deliver the highest business value with the lowest risk.

#### Evaluation Filters:
*   **Automation:** AI completely executes the task (best for high-volume, low-risk, simple rules).
*   **Augmentation:** AI drafts or prepares data, while a human reviewer makes the final call (best for complex decisions and regulated industries).
*   **Decision Support:** AI provides recommendations or risk flags to assist human operators.

---

### 2. Enterprise Framework: The Use Case Evaluation Matrix
```
         High Business Value
         +-------------------------------------+-------------------------------------+
         | 2. COMPLEX SHIFT                    | 1. CORE PILOT                       |
         | (Augmentation / Human-in-the-Loop)   | (RAG, search, metadata extraction)  |
         |                                     |                                     |
V        |                                     |                                     |
a        +-------------------------------------+-------------------------------------+
l        | 4. REJECT / DEFER                   | 3. QUICK WIN                        |
u        | (Low priority, high development)    | (Auto-categorization rules)         |
e        |                                     |                                     |
         |                                     |                                     |
         +-------------------------------------+-------------------------------------+
         Low Business Value           Feasibility               High Feasibility
```

---

### 3. Checklists & Templates
#### Use Case Intake & Evaluation Rubric
```markdown
### Use Case Intake Scorecard
1. **Business Metric (1-5):** [e.g., Score 5: Directly cuts AHT by $1M+/year]
2. **Data Readily Available (1-5):** [e.g., Score 4: Data resides in clean S3 buckets]
3. **Model Feasibility (1-5):** [e.g., Score 4: Standard off-the-shelf models work]
4. **Integration Complexity (1-5):** [e.g., Score 2: Requires custom Salesforce endpoints]
5. **Weighted Total Score:** [(Value * Feasibility) / Complexity] = [Score]
```

---

## Module 4: User Journey Mapping

### 1. Detailed Theory
A User Journey Map documents the operational path of a persona, highlighting their actions, tool touchpoints, pain points, and cognitive shifts at each stage of a process.

```
Journey Stages: [Receipt of Input] ➔ [Verification & Lookup] ➔ [Decision Drafting] ➔ [Manager Sign-off]
```

*   **Moments of Friction:** Points where the user experiences frustration, cognitive overload, or delay (e.g., logging into multiple portals or copying text manually).
*   **Service Blueprinting:** Mapping the visible user actions (front-stage) directly to the supporting backend systems, databases, and APIs (back-stage).

---

### 2. Enterprise Framework: Service Blueprint Template
```
+--------------------+----------------------+---------------------+----------------------+
| Stage              | 1. Input Intake      | 2. Data Check       | 3. Decision Log      |
+--------------------+----------------------+---------------------+----------------------+
| Front-Stage (User) | Uploads PDF claim    | Opens CRM lookup    | Types approval email |
| Back-Stage (Infra) | S3 upload trigger    | Database query      | Updates ERP record   |
| AI Intervention    | Auto-extraction API  | Semantic match RAG  | Generates draft text |
+--------------------+----------------------+---------------------+----------------------+
```

---

## Module 5: Workflow Analysis

### 1. Detailed Theory
Workflow Analysis maps the sequence of manual and automated tasks within a process to calculate process efficiency.

#### Core Analysis Tools:
*   **SIPOC (Suppliers, Inputs, Process, Outputs, Customers):** High-level view of process boundaries.
*   **BPMN (Business Process Model and Notation):** Standardized flowcharting showing decision branches, systems, and user hand-offs.
*   **Process Efficiency Calculation:**
    $$\text{Process Efficiency} = \frac{\text{Value-Add Processing Time}}{\text{Total Cycle Lead Time}} \times 100$$

---

### 2. Checklists & Templates
#### Process Mapping Assessment Checklist
- [ ] Identify and map all decision splits and escalation loops.
- [ ] Note every manual data entry step.
- [ ] Measure queue times between process stages.
- [ ] Count the number of software applications the operator must use to complete a transaction.

---

## Module 6: Current State Assessment

### 1. Detailed Theory
The Current State Assessment audits an organization across four pillars—People, Process, Technology, and Data (PPTD)—to evaluate its readiness for AI integration.

#### PPTD Framework:
*   **People:** Assessment of team skill levels, training needs, and openness to adoption.
*   **Process:** Evaluation of workflow standardization, documentation, and error rates.
*   **Technology:** Audit of existing software, API structures, latency constraints, and hosting capabilities.
*   **Data:** Review of data quality, accessibility, storage security, and indexing maturity.

---

### 2. Enterprise Framework: The AI Maturity Scorecard
```
+------------------+-----------------------------+-----------------------------+-----------------------------+
| Maturity Level   | Level 1: Fragmented         | Level 2: Structured         | Level 3: AI-Ready           |
+------------------+-----------------------------+-----------------------------+-----------------------------+
| Data Pillar      | Legacy paper, no databases  | Relational databases, APIs  | Real-time streams, vector DB|
| Tech Pillar      | On-premise, blocked network | Hybrid cloud, simple APIs   | VPC hosted, scalable micro- |
|                  |                             |                             | services                    |
+------------------+-----------------------------+-----------------------------+-----------------------------+
```

---

## Module 7: Future State Design

### 1. Detailed Theory
Future State Design creates the target operating model, defining how human operators and AI agents will collaborate in the future workflow.

```
Future Workflow: [AI Ingests & Structures] ➔ [AI Drafts Recommendation & Cites] ➔ [Human Reviews & Edits] ➔ [Submit]
```

#### Key Design Principles:
*   **Keep Humans in the Loop (HITL):** Design the UI to support human validation, correction, and final approval of AI suggestions.
*   **Minimize Context Switching:** Embed AI inputs directly into the primary software interface the operator already uses.
*   **Actionable Citations:** Ensure all model extractions link directly to their source documents to support fast verification.

---

### 2. Checklists & Templates
#### Future State Blueprint Outline
- [ ] **Target Workflow Diagram:** Visual roadmap of the updated process.
- [ ] **Role Definition:** Updated descriptions of operator tasks and responsibilities.
- [ ] **System Integration Map:** API connections, database updates, and network flows.
- [ ] **Change Management Plan:** Training schedules, user feedback loops, and deployment phases.

---

## Module 8: Prioritization Frameworks

### 1. Detailed Theory
FDEs use prioritization frameworks to establish a clear, structured roadmap for feature and use case development, preventing scope creep and resource constraints.

#### Prioritization Frameworks:
*   **RICE Framework:**
    $$\text{RICE Score} = \frac{\text{Reach} \times \text{Impact} \times \text{Confidence}}{\text{Effort}}$$
*   **Value vs. Complexity Matrix:** Plotting features by business value against implementation difficulty.
*   **Kano Model:** Categorizing features into Basic Needs, Performance Needs, and Delighters to manage user satisfaction.

---

### 2. Prioritization Matrix Template
```markdown
# Feature Prioritization Matrix: Claims Copilot

| Feature ID | Feature Name | Reach (1-10) | Impact (1-5) | Confidence % | Effort (Person-Weeks) | RICE Score |
| :--- | :--- | :---: | :---: | :---: | :---: | :---: |
| F1 | Citation highlights in PDF | 10 | 4 | 90% | 3 | **12.0** |
| F2 | Automated Email Dispatch   | 10 | 3 | 50% | 8 | **1.8** |
| F3 | Multi-language UI translation| 2 | 1 | 80% | 4 | **0.4** |
```

---

## Module 9: Risk Assessment

### 1. Detailed Theory
Deploying AI at scale introduces risks across multiple categories:
*   **Technical Risk:** Latency spikes, system downtime, model hallucination rates.
*   **Operational Risk:** Low user adoption, broken workflows, manual backup bottlenecks.
*   **Compliance & Security Risk:** PII leakage, regulatory compliance violations, database vulnerabilities.

#### Risk Mitigation:
*   **FMEA (Failure Mode and Effects Analysis):** Identifying potential failure modes, estimating their severity and likelihood, and planning mitigations.
*   **RAID Register:** Continuously tracking Risks, Assumptions, Issues, and Dependencies throughout the project lifecycle.

---

### 2. Enterprise Framework: The FMEA Template
```markdown
# Failure Mode and Effects Analysis (FMEA): Claims Copilot

## Risk Register
| Failure Mode | Severity (1-10) | Likelihood (1-10) | Detection (1-10) | RPN (S*L*D) | Mitigation Action |
| :--- | :---: | :---: | :---: | :---: | :--- |
| Model extracts incorrect exclusion limit. | 8 | 4 | 2 | **64** | Implement citation verification highlights in the UI. |
| DB connection times out during peak hours. | 9 | 3 | 3 | **81** | Implement retry logic and database replica scaling. |
```

---

## Module 10: Constraint Analysis

### 1. Detailed Theory
Every enterprise project operates within constraints. An FDE must analyze these limitations to design a feasible solution.

```
Constraints Model: [Budget Boundaries] ↔ [Technical Limitations] ↔ [Regulatory Compliances]
```

*   **Regulatory Constraints:** Local laws (e.g., GDPR, HIPAA, EU AI Act) defining where data must reside and how it can be processed.
*   **Technical Constraints:** Legacy system code limits, network latency budgets, API bandwidth caps.
*   **Resource Constraints:** Team skills, developer availability, budget, and project timelines.

---

### 2. Constraint Resolution Framework
```
+--------------------+-----------------------------+-----------------------------+
| Constraint         | Direct Impact               | FDE Mitigation Plan         |
+--------------------+-----------------------------+-----------------------------+
| GDPR Compliance    | Client data cannot leave EU | De-identify data locally or |
|                    | borders.                    | host models in EU regions.  |
+--------------------+-----------------------------+-----------------------------+
| 2-Second Latency   | Web tool will lag if model  | Stream text outputs and run |
|                    | completes full generation.  | semantic checks asynchronously.|
+--------------------+-----------------------------+-----------------------------+
```

---

# Enterprise AI FDE Case Studies

---

## Case Study 1: Insurance Claims Automation

### 1. Current State Assessment
An FDE reviewed the claims process for an auto insurer. The assessment showed that claims handlers manually logged into three separate tools to verify claims, leading to an average handle time (AHT) of 28 minutes.

### 2. Workflow Analysis
The FDE mapped the process to find the primary bottleneck:
```
Open Claim ➔ Open Registry Database ➔ Verify Matching Names ➔ Open Invoices ➔ Compare Totals ➔ Log Approval
```
The comparison step took 18 minutes and had a 14% error rate.

### 3. Root Cause Analysis
Using the 5 Whys, the FDE identified that handlers frequently mistyped values when copying data between tools, which led to incorrect claim approvals.

### 4. Future State Design
The FDE designed an integrated UI that extracted name and invoice details automatically and displayed them side-by-side with the CRM record, reducing manual data entry.

---

## Case Study 2: Underwriting Copilot

### 1. Use Case Discovery
A property insurer wanted to improve risk analysis for warehouse safety logs. The FDE evaluated three options, selecting a risk-flagging assistant as the most feasible MVP.

### 2. Prioritization
The FDE ran a RICE analysis to prioritize features, focusing on PDF document search and automated risk alerts.

### 3. Constraint Analysis
The CISO raised concerns about passing safety logs to cloud-hosted APIs. The FDE resolved this by hosting the model within the client's private AWS VPC, satisfying security requirements.

---

## Case Study 3: Customer Support AI Assistant

### 1. User Journey Mapping
The FDE shadowed support agents to map their customer interaction journey. The mapping showed that agents experienced friction when searching for policy exclusion rules, causing long call holds.

### 2. Workflow Optimization
The FDE integrated a semantic search tool directly into the CRM tool window, allowing agents to search policy manuals without opening a separate database.

### 3. Risk Assessment
The FDE created an FMEA, identifying the risk of model hallucinations. The FDE mitigated this by requiring the assistant to cite the source manual page for every response, helping agents verify recommendations.

---

## Case Study 4: Enterprise Knowledge Assistant

### 1. Current State Analysis
A construction engineering firm had project documents spread across SharePoint, file shares, and wikis. An audit showed that engineers spent over 4 hours per week searching for historical project plans.

### 2. Opportunity Assessment
The FDE identified that implementing a RAG search engine could recover these lost hours.

### 3. Future State Blueprint
The FDE designed a search portal that integrated SharePoint and wiki logs, using a reranking model to present engineers with the most relevant project plans.

---

## Case Study 5: Sales Intelligence Copilot

### 1. Business Problem Framing
A sales team wanted to identify cross-sell opportunities within their customer base. The FDE mapped the problem, identifying that customer data was spread across billing logs, CRM histories, and support tickets, making it difficult for reps to prepare for calls.

### 2. Stakeholder Alignment
The FDE aligned the VP of Sales (who wanted to drive conversion rates) and the IT Security Lead (who wanted to protect database credentials).

### 3. Success Criteria Definition
The FDE established clear success metrics:
*   Reduce rep prep time from 4.5 hours to 30 minutes.
*   Maintain a model recommendation accuracy rate above 90%.

---

# AI FDE Deliverables & Reference Guides

Here is how to create, format, and execute key problem-framing deliverables.

---

## 1. Problem Statement Canvas

### Purpose:
Defining the operational challenge, impact, and stakeholders to guide the project scope.

### Template:
```markdown
# Problem Statement Canvas: [Project Name]

## 1. Problem Definition
*   **The Problem is:** [Describe the operational friction]
*   **It affects:** [Identify user personas and stakeholders]
*   **The impact is:** [Quantify the cost, time, or risk penalty]

## 2. Context & Constraints
*   **Core Systems:** [List databases and applications involved]
*   **Security & Compliance:** [Describe data privacy requirements]

## 3. Success Criteria
*   **Target Outcome:** [e.g., Reduce cycle time by 40%]
*   **Measurement Plan:** [Detail how performance will be tracked]
```

---

## 2. Root Cause Analysis Report

### Purpose:
Documenting the drivers of a process failure and identifying resolutions.

### Template:
```markdown
# Root Cause Analysis (RCA) Report: [System/Process Name]

## 1. Executive Summary
*   **Observed Bottleneck:** [Describe the process failure]
*   **Business Impact:** $[Amount] annual cost / [Number] hours lost.

## 2. Diagnostic Investigation
*   **The 5 Whys Analysis:**
    1. Why? -> [Direct cause]
    2. Why? -> [Technical cause]
    3. Why? -> [Operational cause]
    4. Why? -> [Systemic cause]
    5. Why? -> [Root cause]

## 3. Action Plan
*   **Proposed Fix:** [Detail technical/process resolution]
*   **Expected Resolution Timeline:** [Target date]
```

---

## 3. Constraint & Trade-Off Analysis

### Purpose:
Evaluating architectural options against system constraints.

### Template:
```markdown
# Constraint & Trade-Off Report: [System Name]

## 1. Target Constraints
*   **Compliance:** [e.g., GDPR data residency requirements]
*   **Latency:** [e.g., Maximum 2-second response SLA]
*   **Budget:** $[Amount] maximum CAPEX.

## 2. Architecture Comparison
```
+------------------+-----------------------------+-----------------------------+
| Metric           | Option A: Cloud API         | Option B: Private Host      |
+------------------+-----------------------------+-----------------------------+
| Latency          | 1.2 seconds (Met)           | 1.8 seconds (Met)           |
| GDPR Compliance  | High risk (Requires DPA)    | Low risk (Self-contained)   |
| Budget (Setup)   | Low ($15,000)               | High ($85,000)              |
+------------------+-----------------------------+-----------------------------+
```

## 3. Recommendation
Recommend Option B to address GDPR compliance requirements, despite the higher setup costs.
```

---

# Mastering the AI FDE Career: Core Playbook

To succeed as an AI Forward Deployed Engineer:
1.  **Prioritize Business Value First:** Never lead a conversation with the model name or architecture. Lead with the business metric you are improving.
2.  **Code with the Enterprise in Mind:** Assume data is dirty, networks are restricted, and users are skeptical. Build safety and feedback into every pipeline.
3.  **Drive Change, Not Just Code:** A highly accurate model is useless if users refuse to run it. Spend time co-locating with your users to build tools they trust.
