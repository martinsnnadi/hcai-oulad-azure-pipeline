<!--
# Human-Centred AI Data Governance Framework
**Project:** Data Engineering for Human-centred AI Research  
**Academic Supervisor:** Professor Solomon Sunday Oyelere  
**Framework Status:** Active (Initialised Week 5)

---

## 1. Provenance & Lineage Strategy
To ensure accountability, data transformations are strictly decoupled and tracked using Azure Fabric's native Medallion Lakehouse layout.
* **Bronze (Raw Zone)**: Holds unmodified historical OULAD CSV files. Contains direct system identifiers (`id_student`). No analytical tooling or data scientists are granted read access here.
* **Silver (Audited Zone)**: Holds hashed, joined, and demographic-parity-profiled tables.
* **Metadata Tracking**: Every pipeline iteration appends the structural fields `ingestion_timestamp` and `pipeline_version` directly to the active schema to guarantee lineage tracking back to the source HTTP stream.

---

## 2. Versioning via Delta Lake Engine
Data state drift is handled through **Delta Lake storage formats** inside Azure Fabric.
* **Time Travel Capability**: All transformations are recorded in the Delta transaction log (`_delta_log`). This allows the research team to roll back schemas or query data matching the exact state of a prior date block.
* **Code Version Alignment**: Pipeline logic modifications are tracked via main branch commits on GitHub, creating a 1:1 match between processing code and corresponding data table outputs.

---

## 3. Reproducibility Parameters
To ensure research validity and pipeline replication:
* **Deterministic Hashing**: Cryptographic anonymisation scripts utilize a static, repository-secured salt key to guarantee that a student ID translates to the exact same surrogate key across all relational table joins.
* **Schema Enforcement**: Silver and Gold layers utilize strict schema locking to throw critical processing exceptions if data drift or corrupted column structures are detected during runtime.

---

## 4. Security and Privacy Boundaries
* **Identity Protection**: High-risk identifiers (`id_student`) undergo salted SHA-256 tokenisation during the initial Bronze-to-Silver transition.
* **Access Isolation**: Access control lists (ACLs) are configured to restrict model consumption zones. Downstream algorithms interact strictly with the anonymised features residing in the `OULAD_Gold_Curated` lakehouse workspace.

---

## 5. Documentation Lifecycle
* **Live Cataloging**: A central repository data dictionary acts as the single source of truth for attribute meanings, data types, and equity tracking categories.
* **Pipeline Audit Trails**: All programmatic pipeline halts caused by demographic underrepresentation or severe bias variance trigger automated log notifications to the `Supervisor_Review_Audit_Log`.
-->
