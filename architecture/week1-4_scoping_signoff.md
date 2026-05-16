<!--
# Internship Milestone: Weeks 1–4 Scoping & Design Sign-off
**Project Title:** Data Engineering for Human-centred AI Research  
**Intern:** Martins Ifeanyi Nnadi  
**Academic Supervisor:** Professor Solomon Sunday Oyelere  

---

## 1. Personal Development Goals Note (One-Page Summary)

My technical and research objectives for this 12-week internship are structured around the core pillars of Human-Centered AI engineering:

*   **Goal 1: Medallion Architecture Mastery (Technical)**
    *   *Objective:* Design and deploy functional Bronze and Silver lakehouse environments within Azure Fabric to cleanly separate unvetted data from human-centric consumption layers.
*   **Goal 2: Cryptographic Privacy Engineering (Security)**
    *   *Objective:* Successfully implement robust, salted SHA-256 tokenisation protocols on student identifiers (`id_student`) within a PySpark pipeline to protect individual anonymity.
*   **Goal 3: Algorithmic Fairness Auditing (Ethical)**
    *   *Objective:* Gain production-level familiarity with the `Fairlearn` toolkit. I will programmatically measure Demographic Parity Differences across sensitive student cohorts (disability and age bands) to block biased datasets from downstream consumption.
*   **Goal 4: Git-Driven Collaboration (Professional)**
    *   *Objective:* Maintain a strictly version-controlled GitHub repository utilising declarative JSON environment manifests and descriptive documentation to replicate an enterprise open-science environment.

---

## 2. Working Environment & Access Ledger

### 2.1 Confirmed Environment Status
*   **Version Control Workspace:** Active public GitHub repository initialised with a clean directory structure matching standard data engineering lifecycles.
*   **Cloud Processing Workspace:** Azure Fabric Workspace `OULAD_DENG_HCAI_RESEARCH` established.
*   **Storage Framework:** Isolated `OULAD_DENG_Bronze_Raw` and `OULAD_DENG_Silver_Audited` lakehouses successfully provisioned.

### 2.2 Active Access Issues & Blockers Ledger
*   *Issue 1 (Fabric Capacity):* Direct PySpark notebook compute allocation is running on a temporary trial tier. I want to migrate to paid without losing progress at the end of the 60-day trial.
*   *Issue 2 (Target Access Controls):* Read-access to the Silver lakehouse layer needs explicit role scoping policies applied to prevent unauthorized model training over unvetted attributes.

---

## 3. Supervision Agenda Questions (For Professor Oyelere)

The following structured questions have been prepared to guide our next supervisory meeting as we transition from design to active engineering:

1.  **Bias Threshold Limits:** In our design architecture pack, I implemented a baseline 15% discrepancy limit on the Demographic Parity Difference for the `disability` attribute. Does this line up with your research benchmarks for OULAD learning analytics?
2.  **Privacy Granularity:** When managing the daily Virtual Learning Environment (VLE) interaction logs, do you recommend storing raw daily timestamps, or should we aggregate them into weekly/modular totals to lower individual tracking vulnerabilities?
3.  **Gold Layer Downstream Intent:** Is our target machine learning consumption model focused strictly on classification (predicting dropout risk) or will we need to design features that support clustering for behavioral student profiling?
-->
