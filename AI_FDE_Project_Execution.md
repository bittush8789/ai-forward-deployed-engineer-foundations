# AI Forward Deployed Engineer (AI FDE) Fundamentals: AI Project Execution



This document serves as the comprehensive master reference manual for **Phase 7: AI Project Execution**, taking you from beginner concepts to enterprise-grade execution in Proof of Concept (PoC) planning, MVP scoping, milestone definition, agile delivery frameworks, user validation, change management, risk registers, and executive progress reporting.

---

# Phase 7: AI Project Execution

---

## Module 1: Proof of Concept (PoC) Planning

### 1. Detailed Theory & Taxonomy
A Proof of Concept (PoC) is a short-term, low-cost experiment designed to test a technical hypothesis (e.g., "A retrieval model can identify policy exclusions in PDF manuals with >90% recall") before investing in full-scale integration.

#### Core PoC Guidelines:
*   **Timeboxed Execution:** PoCs are typically restricted to 2 to 4 weeks to keep focus tight.
*   **Hypothesis-Driven Design:** Every PoC must test a specific, measurable technical question.
*   **No Integration Overhead:** Avoid complex database integrations or custom UI designs during this phase. Focus solely on model logic using static data dumps.

---

### 2. Enterprise Framework: The PoC Evaluation Framework
FDEs evaluate PoC outcomes using three target filters:
```
+------------------+-----------------------------+-----------------------------+
| Filter           | Question                    | Target Threshold            |
+------------------+-----------------------------+-----------------------------+
| Feasibility      | Can the model reason over   | Retrieval Recall >90%       |
|                  | unstructured policy text?   |                             |
+------------------+-----------------------------+-----------------------------+
| Accuracy         | Does the model draft correct| Ground truth matching >85%  |
|                  | answers with citations?     |                             |
+------------------+-----------------------------+-----------------------------+
| Performance      | Can inference complete under| Response time <3 seconds    |
|                  | target SLAs?                |                             |
+------------------+-----------------------------+-----------------------------+
```

---

### 3. Checklists & Templates
#### PoC Charter Template
```markdown
# PoC Charter: Underwriting Risk Finder

## 1. Objective & Hypothesis
*   **Hypothesis:** An embedding model can extract structural risk exclusions from building logs with >90% recall.
*   **Duration:** 3 weeks (Start: [Date] | End: [Date]).

## 2. Scope & Data Requirements
*   **In-Scope:** Testing 100 historical PDF inspection logs from Area A.
*   **Out-of-Scope:** Custom frontend developments, ERP database integrations.
*   **Data Owner:** [Name / Department].

## 3. Success Metrics
| Metric | Baseline | Target | Evaluation Method |
| :--- | :--- | :--- | :--- |
| Extraction Recall | N/A | >90% | Ground truth comparison |
| Latency | N/A | <3.0s | Telemetry logs |
```

---

## Module 2: MVP Planning

### 1. Detailed Theory
An MVP (Minimum Viable Product) is the first deployable version of the software that is integrated with production systems and tested by actual users. Unlike a PoC (which is a standalone test), an MVP must be usable in the live business environment.

```
PoC (Tests technical viability) ➔ MVP (Tests workflow integration & user adoption)
```

#### MVP Planning Priorities:
*   **Feature Prioritization:** Use frameworks like MoSCoW or RICE to focus on the essential features that prove business value.
*   **Workflow Alignment:** Ensure the MVP fits smoothly into the operator's daily routine, reducing change resistance.
*   **Outcome Tracking:** Set baseline metrics to measure processing speeds and user adoption rates.

---

### 2. Checklists & Templates
#### MVP Feature Prioritization Matrix
```markdown
# MVP Prioritization Worksheet: Claims Copilot

| Feature Description | Value (1-5) | Complexity (1-5) | Priority (MoSCoW) | Target Release |
| :--- | :---: | :---: | :---: | :--- |
| Search manual via RAG | 5 | 2 | Must Have | Phase 1 (MVP) |
| Highlight citations  | 5 | 3 | Must Have | Phase 1 (MVP) |
| Send email drafts    | 4 | 5 | Should Have| Phase 2 (Scale) |
| Custom UI themes     | 1 | 1 | Won't Have | Deferred |
```

---

## Module 3: Project Scoping

### 1. Detailed Theory
Project Scoping establishes the boundaries of the implementation, documenting what is in-scope, what is out-of-scope, and the dependencies on other teams.

#### Scoping Categories:
*   **In-Scope:** The specific features, databases, and user groups included in the deployment.
*   **Out-of-Scope:** Explicitly documented exclusions to prevent scope creep (e.g., "The system will not translate documents to foreign languages during Phase 1").
*   **Dependencies:** External requirements from other teams (e.g., "Database API endpoints must be opened by the Salesforce team before Week 3").

---

### 2. Scoping Canvas Template
```markdown
# Project Scope Document: [Project Name]

## 1. Project Scope Boundaries
*   **In-Scope:** [Describe included features, systems, and user cohorts]
*   **Out-of-Scope:** [Describe excluded systems, regions, and data formats]

## 2. Assumptions & Constraints
*   *Assumption 1:* Client will provide clean API access to historical logs by Week 2.
*   *Constraint 1:* System must run within the client's secure VPC network.

## 3. Dependency Register
| ID | Dependency Description | Owner | Target Date | Impact if Delayed |
| :--- | :--- | :--- | :---: | :--- |
| D1 | Security review approval for local GPU hosting. | IT Security | Week 2 | Delays deployment by 3 weeks. |
```

---

## Module 4: Milestone Definition & Stage Gates

### 1. Detailed Theory
Milestones define the key progress checkpoints and delivery phases of the project, using stage gates to verify success before moving forward.

```
[Discovery Complete] ➔ [PoC Approval] ➔ [Design Sign-off] ➔ [MVP Rollout] ➔ [Scale & Hand-off]
```

#### Stage Gates:
Verification reviews where technical and business leaders audit results (e.g., checking that the PoC reached the 90% recall target) before approving the next phase of development.

---

### 2. Milestone Planning Template
```markdown
# Milestone Plan: Claims Copilot Rollout

## Milestone 1: Technical Discovery Complete
*   **Target Date:** Week 2.
*   **Success Criteria:** API endpoints mapped, data samples verified.
*   **Stage Gate:** IT Architect sign-off on system connectivity.

## Milestone 2: PoC Hypothesis Validated
*   **Target Date:** Week 5.
*   **Success Criteria:** Model extraction recall reaches >90% on test data.
*   **Stage Gate:** Business Sponsor approval to begin MVP integration.
```

---

## Module 5: Delivery Planning & Agile Methods

### 1. Detailed Theory
Delivery Planning structures the software development process using Agile methodologies, sprint schedules, and capacity planning.

#### Agile Frameworks:
*   **Scrum:** Structured development sprints (typically 2 weeks) with daily standups, sprint planning, and reviews.
*   **Kanban:** Continuous flow tracking using visual boards to limit work-in-progress (WIP) and optimize delivery speeds.
*   **Hybrid Delivery:** Combining structured milestone planning (for budgeting and scoping) with agile sprints (for actual development).

---

### 2. Sprint Roadmap Template
```markdown
# Sprint Delivery Plan: Claims Copilot

## Sprint 1: Data Ingestion & Indexing (Weeks 1 - 2)
*   **Goals:** Configure document parsing pipelines and set up RAG indices.
*   **WIP Limits:** Max 3 active development tasks.

## Sprint 2: Model Orchestration & UI Wireframe (Weeks 3 - 4)
*   **Goals:** Write prompt orchestration logic and build the split-screen UI.
*   **Deliverable:** Working UI widget running model queries in a dev environment.
```

---

## Module 6: Iterative Development & Retrospectives

### 1. Detailed Theory
Iterative Development uses feedback loops and continuous refinement to improve model accuracy and user experience.

#### Agile Feedback Loop:
```
[Deploy Iteration] ➔ [Gather User Feedback / Query Logs] ➔ [Identify Failures] ➔ [Refine Prompts/Index] ➔ [Redeploy]
```

*   **Sprint Reviews:** Demonstrating functional features to stakeholders at the end of each sprint to gather early feedback.
*   **Retrospectives:** Reviewing team performance to identify and resolve workflow bottlenecks (e.g., "DB credential delays are blocking developer progress").

---

## Module 7: User Validation & UAT

### 1. Detailed Theory
User Validation and User Acceptance Testing (UAT) verify that the system functions correctly in the live workflow and meets user requirements before launch.

#### UAT Categories:
*   **Functional UAT:** Verifying that features work as intended (e.g., "The citation highlights match the correct source page").
*   **Performance UAT:** Testing response times and system stability under peak loads.
*   **Adoption Validation:** Tracking daily usage volumes and user satisfaction ratings during pilot phases.

---

### 2. Checklists & Templates
#### UAT Checklist: Claims Copilot
- [ ] Confirm that all test scenarios have been documented and reviewed.
- [ ] Verify that test data samples are loaded into the UAT database environment.
- [ ] Train the pilot group handlers on how to log issues in the tracking tool.
- [ ] Set up daily triage meetings to review and prioritize logged defects.

---

## Module 8: Change Request Management

### 1. Detailed Theory
Change Request Management handles requests for modifications to the project scope, timeline, or budget through a structured impact analysis and approval workflow.

#### Change Control Board (CCB):
The review committee (FDE, Business Sponsor, IT Lead) that evaluates change requests to decide whether to approve, defer, or reject them.

---

### 2. Enterprise Framework: The Change Assessment Matrix
```
+--------------------+-----------------------------+-----------------------------+-----------------------------+
| Change Request     | Scope/Schedule Impact       | Resource/Cost Impact        | Recommendation              |
+--------------------+-----------------------------+-----------------------------+-----------------------------+
| Add voice-to-text  | Adds 4 weeks to timeline    | Requires additional developer| Defer to Phase 2            |
| notes.             |                             | and API budget              |                             |
+--------------------+-----------------------------+-----------------------------+-----------------------------+
| Include signature  | Adds 3 days to development  | Minimal                     | Approve for MVP             |
| templates.         |                             |                             |                             |
+--------------------+-----------------------------+-----------------------------+-----------------------------+
```

---

### 3. Change Request Template
```markdown
# Change Request Form: CR-[Number]

## 1. Request Description
*   **Requested Change:** [Describe the proposed modification]
*   **Reason for Change:** [Describe the operational value or requirement]

## 2. Impact Analysis
*   **Timeline Impact:** [e.g., Adds 1 week to Sprint 3]
*   **Budget Impact:** $[Amount] additional API costs.

## 3. CCB Decision
*   **Status:** [ ] Approved [ ] Deferred [ ] Rejected
*   **Sponsor Signature:** ___________________________
```

---

## Module 9: Risk Management

### 1. Detailed Theory
Risk Management involves identifying, evaluating, and mitigating risks across business, delivery, and technical categories.

#### Risk Classifications:
*   **Business Risks:** Stakeholder resistance, low user adoption, budget reallocations.
*   **Delivery Risks:** Developer constraints, timeline delays, scope creep.
*   **Technical Risks:** Data quality issues, API downtime, model reasoning errors.

---

### 2. Risk Register Template
```markdown
# Risk Register: Project Claims Copilot

| Risk ID | Risk Description | Category | Likelihood | Impact | Mitigation Plan | Owner |
| :--- | :--- | :--- | :---: | :---: | :--- | :--- |
| R1 | Data sample formatting is inconsistent. | Technical | High | High | Build data normalization preprocessing scripts. | FDE Lead |
| R2 | IT Security delays API approvals. | Delivery | Medium | High | Escalate dependency during weekly syncs. | IT Sponsor |
```

---

## Module 10: Project Tracking & Dashboards

### 1. Detailed Theory
Project Tracking monitors project progress, timelines, and budgets, sharing status reports with stakeholders and executives.

#### Project Metrics:
*   **Schedule Variance (SV):** The difference between planned and actual progress.
*   **Budget Variance (BV):** The difference between planned and actual expenditures.
*   **Adoption Rate:** The percentage of target users active on the system.

---

### 2. Weekly Status Report Template
```markdown
# Weekly Status Report: Claims Copilot

## 1. Project Health Summary
*   **Overall Status:** [ ] Green [ ] Yellow [ ] Red
*   **Schedule Status:** On track (Sprint 2 complete).
*   **Risk Level:** Low (No active blockers).

## 2. Milestone Tracking
*   Milestone 1: Technical Discovery Complete [x]
*   Milestone 2: PoC Hypothesis Validated [x]
*   Milestone 3: MVP Integration Pilot [/] (In-progress)

## 3. Key Accomplishments (This Week)
*   Completed the RAG pipeline integration.
*   Configured visual highlights for page citations in the PDF viewer.
```

---

# Enterprise AI FDE Case Studies

---

## Case Study 1: Insurance Underwriting Copilot

### 1. PoC Planning
The FDE planned a 3-week PoC to test whether the model could extract risk exclusions from building logs, setting a success target of >90% recall.

### 2. MVP Definition
Following PoC validation, the FDE defined the MVP scope, focusing on document search and citation tooltips, and deferring automated report exports to Phase 2.

### 3. Risk Management & Reporting
The FDE managed risks (e.g., data formatting discrepancies) using a RAID log, and shared weekly progress dashboards to keep the executive sponsors aligned.

---

## Case Study 2: Claims Processing Automation

### 1. Project Scoping
The FDE scoped the claims pipeline integration, establishing Guidewire data access as a key dependency and documenting manual payment authorizations as out-of-scope for the MVP.

### 2. Delivery Planning & UAT
The FDE managed development using 2-week sprints and ran a 2-week UAT pilot with 10 claims handlers, resolving system issues before launch.

---

## Case Study 3: Enterprise Knowledge Assistant

### 1. Iterative Development
The FDE managed development using Agile sprints, refining the RAG retrieval logic based on user search logs.

### 2. Change Management & Adoption
To drive adoption, the FDE trained power users to run weekly demos, helping the assistant reach **85% active usage** within 4 weeks of rollout.

---

## Case Study 4: Customer Support AI Assistant

### 1. Milestone Planning
The FDE structured the project into 4 key milestones, setting target response latency times as a stage gate before MVP deployment.

### 2. UAT Execution
During UAT, support agents flagged that the system struggled with shorthand query terms. The FDE updated the search indexing with a synonym dictionary to resolve the issue.

---

## Case Study 5: Sales Intelligence Copilot

### 1. Outcome Tracking
The FDE configured the tool to track usage metrics and prep times automatically, showing that the system saved reps an average of **4 hours per week**.

### 2. Success Measurement
The FDE compiled these metrics into a value realization report for the VP of Sales, demonstrating the project's impact and securing budget for full rollout.

---

# AI FDE Deliverables & Reference Guides

Here is how to create, format, and execute key execution deliverables.

---

## 1. Project Scope Document

### Purpose:
Defining project boundaries, in-scope requirements, assumptions, and dependencies.

### Template:
```markdown
# Project Scope Document: [Project Name]

## 1. Scope Boundaries
*   **In-Scope:** [Detail features, databases, and user groups included]
*   **Out-of-Scope:** [Detail excluded features and systems]

## 2. Dependencies & Assumptions
*   **Critical Dependency:** [e.g., Database access granted by Week 2]
*   **Key Assumption:** [e.g., Target users will participate in UAT sessions]

## 3. Project Risks
*   *Risk 1:* [Describe risk and mitigation action]
```

---

## 2. UAT Plan & Script

### Purpose:
Structuring user validation scenarios to verify system functionality.

### Template:
```markdown
# UAT Test Plan: [Project Name]

## 1. Test Profile
*   **Tester Name:** [Name] | **User Role:** [e.g., Claims Handler]
*   **Test Date:** [Date] | **UAT Environment Version:** [Version]

## 2. Test Scenarios
*   **Scenario 1: Document Upload & Parsing**
    *   *Step 1:* Upload sample PDF report.
    *   *Step 2:* Verify metadata values extract correctly.
    *   *Expected Result:* Values match original document text.
    *   *Actual Status:* [Pass / Fail]

## 3. Defect Log
| ID | Defect Description | Severity | Target Resolution Date |
| :--- | :--- | :---: | :--- |
| DF1 | Page highlights are offset by one line. | Medium | Week 4 |
```

---

## 3. Change Request Log

### Purpose:
Tracking scope changes, impact evaluations, and CCB decisions.

### Template:
```markdown
# Change Request Log: [Project Name]

| CR ID | Request Description | Raised By | Status | Schedule Impact | Decision Date |
| :--- | :--- | :--- | :---: | :--- | :---: |
| CR1 | Add automated summary export to CRM. | Ops Lead | Deferred | Adds 3 weeks to timeline | [Date] |
| CR2 | Configure custom email signatures. | Team Champion| Approved | Adds 2 days to timeline  | [Date] |
```

---

# Mastering the AI FDE Career: Core Playbook

To succeed as an AI Forward Deployed Engineer:
1.  **Prioritize Business Value First:** Never lead a conversation with the model name or architecture. Lead with the business metric you are improving.
2.  **Code with the Enterprise in Mind:** Assume data is dirty, networks are restricted, and users are skeptical. Build safety and feedback into every pipeline.
3.  **Drive Change, Not Just Code:** A highly accurate model is useless if users refuse to run it. Spend time co-locating with your users to build tools they trust.
