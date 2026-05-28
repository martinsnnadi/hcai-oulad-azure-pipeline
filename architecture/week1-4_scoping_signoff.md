<!--
# Internship Milestone: Weeks 1–4 Scoping & Design Sign-off
**Project Title:** Data Engineering for Human-centred AI Research  
**Intern:** Martins Ifeanyi Nnadi  
**Academic Supervisor:** Professor Solomon Sunday Oyelere  
**Framework Horizon:** 24-Week Structured Research & Development Timeline

---

## 1. Personal Development Goals Note (One-Page Summary)

My technical, ethical, and research objectives for this 24-week academic supervision internship are structured around my existing multi-cloud skillset—bridging my Microsoft Fabric Data Engineer Associate (DP-600) certification, AWS/Snowflake bootcamp tracks, and Human-Centered AI (HCAI) engineering:

*   **Goal 1: Advanced Medallion Architecture Implementation (Technical)**
    *   *Objective:* Design and provision fully segregated Bronze, Silver, and Gold lakehouse environments within the Azure Fabric workspace to isolate raw, unvetted education datasets from downstream machine learning consumers.
*   **Goal 2: Complex Data Profiling & Time-Series Wrangling (Analytical)**
    *   *Objective:* Programmatically transform, clean, and resolve anomalies within the Open University Learning Analytics Dataset (OULAD). I will write PySpark window functions to compress 10.6 million asynchronous clickstream log entries into uniform, weekly analytical feature layers.
*   **Goal 3: Cryptographic Privacy & Security Engineering (Security)**
    *   *Objective:* Enforce data-at-rest anonymisation by developing a deterministic, salted SHA-256 tokenisation pipeline over primary student keys (`id_student`), hiding secret environment salts to eliminate individual re-identification vulnerabilities.
*   **Goal 4: Algorithmic Equity Auditing & Data Governance (Ethical)**
    *   *Objective:* Master the operational integration of the `Fairlearn` toolkit. I will hardcode automated pipeline validation blocks checking historical Demographic Parity Differences across protected student cohorts (such as disability and age groups).
*   **Goal 5: Multi-Cloud Integration & Code-to-Data Alignment (Professional)**
    *   *Objective:* Establish 1:1 version control alignment by injecting GitHub commit hashes directly into Delta Lake transaction logs (`_delta_log`), maintaining a reproducible, auditable open-science workflow while cross-referencing cloud design patterns learned via AWS/Snowflake.

---

## 2. Working Environment & Access Ledger

### 2.1 Confirmed Environment Status
*   **Version Control Workspace:** Active public GitHub cloud repository (`hcai-oulad-azure-pipeline`) fully initialized with explicit directory routing (`architecture/`, `notebooks/`, `config/`).
*   **Cloud Processing Workspace:** Microsoft Azure Fabric corporate workspace `OULAD_HCAI_Analytics` established.
*   **Storage Framework:** Complete 3-tier Medallion architecture successfully provisioned as decoupled infrastructure points:
    1. `OULAD_Bronze_Raw` (Immutable append-only landing zone for education CSV tables).
    2. `OULAD_Silver_Audited` (Anonymised, joined, and fairness-vetted Delta tables).
    3. `OULAD_Gold_Curated` (Aggregated, semantic student feature matrices optimized for unbiased Power BI reporting and AI consumption).

### 2.2 Active Access Issues & Blockers Ledger
*   *Issue 1 (Fabric Capacity Migration):* Direct PySpark notebook compute allocation is running on a temporary cloud trial tier. We must schedule a migration roadmap to a stable research capacity before the 60-day trial window expires to maintain runtime integrity.
*   *Issue 2 (Granular Role Scoping Policies):* While workspace Access Control Lists (ACLs) successfully add Professor Oyelere with remote validation visibility, explicit Column-Level Security (CLS) and Row-Level Security (RLS) rules need to be written to prevent downstream analytics from accessing raw sensitive fields before anonymisation.

---

## 3. Supervision Agenda Questions (For Professor Oyelere)

The following structured questions have been prepared to guide our next active supervision session as we officially transition from the design phase to Week 5 data ingestion:

1.  **Bias Threshold Thresholds:** In our design architecture pack, I implemented a baseline 15% discrepancy limit on the Demographic Parity Difference for the `disability` and `age_band` attributes. Does this specific margin align with your learning analytics research benchmarks, or should the gatekeeper threshold be tightened?
2.  **Temporal Privacy Granularity:** The OULAD click logs track granular, daily student interaction timestamps. To lower individual behavior tracking vulnerabilities, do you recommend aggregating these log counts into uniform weekly modules, or should we retain daily intervals for specific feature distributions?
3.  **Gold Layer Semantic Intention:** To help me design the final tables inside `OULAD_Gold_Curated`, is the target consuming machine learning model intended for classification tasks (predicting immediate student dropout risk) or will we need to design features that support unsupervised clustering for behavioral student profiling?
4.  **Provenance Metadata Architecture:** For our Code-to-Data alignment strategy, do you prefer the pipeline to inject the raw GitHub commit hash string directly into the schema metadata columns, or should we maintain a standalone markdown compliance registry file inside the repository root?
-->
