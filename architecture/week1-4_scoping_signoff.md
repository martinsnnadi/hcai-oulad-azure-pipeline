# Internship Milestone: Weeks 1–4 Scoping & Design Sign-off

**Project**: Data Engineering for Human-Centred AI Research  
**Intern**: Martins Ifeanyi Nnadi  
**Supervisor**: Prof. Solomon Sunday Oyelere  
**Horizon**: 24-Week Parallel Processing Research Roadmap

---

## 1. Personal Development Goals Note (One-Page Summary)

Technical, ethical, and research objectives leveraging Microsoft Fabric (DP-600), AWS/Snowflake bootcamp proficiencies, and HCAI engineering design principles:

*   **Goal 1: Advanced Medallion Architecture Implementation (Technical)**
    *   *Objective*: Provision decoupled Bronze, Silver, and Gold lakehouses in Azure Fabric to isolate raw historical datasets from machine learning consumers.
*   **Goal 2: Complex Data Profiling & Time-Series Wrangling (Analytical)**
    *   *Objective*: Use PySpark window functions to aggregate 10.6M+ asynchronous clickstream entries from OULAD into weekly analytical feature layers.
*   **Goal 3: Cryptographic Privacy & Security Engineering (Security)**
    *   *Objective*: Deploy deterministic, salted SHA-256 tokenisation over primary student keys (`id_student`), isolating secret environment salts to eliminate re-identification.
*   **Goal 4: Algorithmic Equity Auditing & Data Governance (Ethical)**
    *   *Objective*: Integrate the `Fairlearn` toolkit. Hardcode pipeline execution checks to monitor Demographic Parity Differences across disability and age cohorts.
*   **Goal 5: Multi-Cloud Integration & Reproducibility (Professional)**
    *   *Objective*: Inject GitHub commit hashes into Delta transaction logs (`_delta_log`) for 1:1 code-to-data alignment while cross-referencing AWS/Snowflake pipeline patterns.

---

## 2. Working Environment & Access Ledger

### 2.1 Confirmed Environment Status
*   **Version Control**: Active GitHub cloud repository (`hcai-oulad-azure-pipeline`) with standard directories (`architecture/`, `notebooks/`, `config/`).
*   **Cloud Processing**: Microsoft Azure Fabric corporate workspace `OULAD_DENG_HCAI_Analytics` operational.
*   **Storage Infrastructure**: Provisioned 3-tier Medallion architecture:
    1.  `OULAD_DENG_Bronze_Raw` (Immutable append-only CSV landing zone).
    2.  `OULAD_DENG_Silver_Audited` (Anonymised, joined, and fairness-vetted Delta tables).
    3.  `OULAD_DENG_Gold_Curated` (Aggregated student feature matrices optimised for unbiased Power BI and AI model consumption).

### 2.2 Active Access Issues & Blockers Ledger
*   *Issue 1 (Fabric Capacity Migration)*: PySpark notebook compute running on a temporary cloud trial tier. Requires migration to a stable research capacity before the 60-day window expires.
*   *Issue 2 (Cross-Organisational Access Blocker)*: Fabric tenant policies block external domain invitations. The platform prevents adding Prof. Oyelere's institutional account directly to the workspace ACL.

---

## 3. Supervision Agenda Question (For Professor Oyelere)

1. **Clickstream Privacy Granularity**: The raw OULAD data tracks specific daily student click interactions. To protect user identities and mitigate individual tracking risks, do you prefer the pipeline aggregate these logs into weekly totals during processing, or should we ingest the raw daily intervals as-is?
