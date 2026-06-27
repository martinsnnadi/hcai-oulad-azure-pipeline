# OULAD Dataset Evaluation & Strategic Scoping

**Project**: Data Engineering for Human-Centred AI Research  
**Supervisor**: Prof. Solomon Sunday Oyelere  
**Status**: Completed Evaluation  

---

## 1. Access, Licensing & Volume Statistics

Publicly sourced via the Open University’s Knowledge Media Institute (KMi) portal. Released under the **Creative Commons Attribution 4.0 International (CC BY 4.0)** license. 

The raw archive size evaluates to **~155 MB compressed (expanding to ~420 MB uncompressed text sheets)**. It contains no raw Personally Identifiable Information (PII), neutralizing GDPR compliance barriers for sandbox staging.

### In-Depth Database Size & Row Metrics
The relational footprint spans **7 interconnected CSV modules** with the following definitive inventory counts:
*   `studentVle`: **10,655,280 rows** (Granular student clickstream interaction logs).
*   `studentAssessment`: **173,912 rows** (Student module test results).
*   `studentInfo`: **32,593 rows** (Core student demographic and registry snapshot table).
*   `studentRegistration`: **32,593 rows** (Course onboarding and withdrawal timestamps).
*   `vle`: **6,364 rows** (Virtual Learning Environment structural material resource catalog).
*   `assessments`: **206 rows** (Module grading rule specifications).
*   `courses`: **22 rows** (Module timeline metadata).

---

## 2. Technical Profile & Engineering Opportunities

OULAD forms an unnormalised relational star schema. Working with it enables advanced database pattern testing:
*   **Relational Joins**: Linking high-volume activity tables to low-volume dimensional student snapshots via composite composite keys (`id_student`, `code_module`, `code_presentation`).
*   **Window Functions**: Building PySpark partitions to aggregate millions of asynchronous daily rows into weekly behavioral vectors.
*   **Time-Series Tracking**: Synchronizing discrete assignment deadline events against continuous, irregular click streams.
*   **Medallion Engineering**: Transforming loose flat CSV files into high-performance, managed Delta Lake tables inside Azure Fabric [4].

---

## 3. Research Relevance & Ethical AI Grounding

Directly supports Prof. Oyelere’s focus on hybrid intelligence systems and equitable educational technology. The dataset contains vital protected identity traits to run **algorithmic fairness, predictive bias, and responsible AI** audits:
*   `gender` (Biological profile).
*   `disability` (Medical registration status).
*   `age_band` (Generational assignment classification).
*   `imd_band` (Index of Multiple Deprivation regional socio-economic proxy).

These fields let us integrate **Fairlearn** checkpoints in the Silver layer, ensuring early-dropout prediction models don't auto-penalize vulnerable student cohorts.

---

## 4. Data Quality Challenges (The Mitigation Strategy)

OULAD contains major real-world data tracking errors that the pipeline must catch and mitigate:
*   **Sparse / Null Values**: `date_unregistration` is left blank for completing students; `imd_band` contains unpopulated cells. Checked via custom null-parsing metrics.
*   **Class Imbalance**: Students with a documented disability represent only **~10% of the active cohort**. Handled via programmatic fairness screening to prevent model underrepresentation bias.
*   **Asynchronous Timestamps**: Interaction events use relative day offsets (Day -30 up to Day 269) relative to module starts. Fixed by building normalized epoch metrics during ingestion.

---

## 5. Portfolio & Architectural Value

Proves production-grade, enterprise-ready cloud data warehousing capabilities:
*   **Architecture**: Deploys a full Medallion layout (Bronze → Silver → Gold) entirely inside Microsoft Fabric.
*   **Advanced Patterns**: Builds real-world big-data transforms, structural data type locks (`StructType`), and feature aggregation layers at scale.
*   **HCAI Frameworks**: Integrates salted SHA-256 tokenization, metadata data lineage logging, and Fairlearn parity auditing loops.

---

## 6. References

1. Kuzilek, J., Hlosta, P. and Zdrahal, Z. (2017) 'Open University Learning Analytics Dataset', *Scientific Data*, 4(1).
2. Oyelere, S. S., et al. (2024) 'A Scoping Review of Hybrid Intelligence Systems for Human-Centred AI in Education', *Computers in Human Behavior*, 150.
3. Shneiderman, B. (2021) 'Human-Centered Artificial Intelligence: Reliable, Safe & Trustworthy', *IJHCI*, 37(6).
4. Armbrust, M., et al. (2020) 'Delta Lake: High-Performance ACID Table Storage over Cloud Object Stores', *VLDB*, 13(12).
