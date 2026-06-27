# Human-Centred AI Data Governance Framework

**Project**: Data Engineering for Human-Centred AI Research  
**Supervisor**: Prof. Solomon Sunday Oyelere  
**Status**: Active

---

## 1. Provenance & Lineage Strategy

Uses Azure Fabric's Medallion Lakehouse layout to isolate data states and ensure complete lineage accountability.
*   **Bronze (Raw)**: Unmodified historical OULAD records with direct system IDs (`id_student`). Closed to analytical tools and data scientists.
*   **Silver (Audited)**: Cryptographically de-identified, hashed, joined, and demographic-parity-profiled tables.
*   **Gold (Curated)**: Optimised semantic feature matrices and aggregated views. Only layer accessible by downstream AI training and Power BI DirectLake dashboards.
*   **Metadata Tracking**: Appends non-nullable `PIPELINE_INGEST_TS` and `SOURCE_FILE_NAME` lineage fields to active schemas to trace records back to source extraction events.

---

## 2. Versioning via Delta Lake Engine

Manages data state drift and schema consistency natively inside Azure Fabric via Delta Lake.
*   **Time Travel**: Transaction logging (`_delta_log`) records all changes, allowing the pipeline to roll back schemas or query precise historical data states.
*   **Code Versioning**: Syncs processing code changes to main branch GitHub commits to maintain a 1:1 match between pipeline logic and data outputs.

---

## 3. Reproducibility Parameters

*   **Deterministic Hashing**: Cryptographic tokenisation uses a static, repository-secured salt key to ensure student IDs resolve to matching surrogate keys across relational table joins.
*   **Schema Enforcement**: Applies strict schema structural locks in Silver and Gold layers to halt processing if runtime column drift or corrupted fields are detected.

---

## 4. Security and Privacy Boundaries

*   **Identity Protection**: Salts and hashes high-risk identifiers (`id_student`) via SHA-256 during the initial Bronze-to-Silver transition layer.
*   **Access Isolation**: Enforces explicit Cloud Access Control Lists (ACLs). Restricts downstream training models to anonymised features in the `OULAD_Gold_Curated` layer.

---

## 5. Documentation Lifecycle

*   **Data Cataloguing**: Uses a central repository data dictionary to map attribute metadata, data types, and equity metrics.
*   **Pipeline Audits**: Directs automated log notifications to `Supervisor_Review_Audit_Log` if underrepresentation or bias variance triggers a pipeline execution halt.
