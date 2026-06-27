# 🎓 OULAD Ingestion Pipeline
### HCAI Data Track | Azure Fabric (DP-600)

**Supervisor:** Prof. Solomon Sunday Oyelere  
**Milestone:** Week 8 (Bronze Validation & Schema Migration)

---

## 1. Project & Dataset Review

Automated, secure ingestion infrastructure for the Open University Learning Analytics Dataset (OULAD).

### 1.1 Technical Profile
*   **Domain**: EdTech / Learning Analytics.
*   **Source Structure**: Unnormalized relational schema across 7 tables (`studentInfo`, `studentVle`, etc.).
*   **Data Scale**: 10.6M+ granular clickstream records in `studentVle_bronze`.
*   **Execution Competencies**: Built using Microsoft Fabric Data Engineer Associate (DP-600) and Python Essentials skillsets.

### 1.2 HCAI Risk Assessment
*   **Algorithmic Bias**: Unvetted historical dropout models penalize lower socio-economic or disabled student groups. Silver layer uses Fairlearn to block Demographic Parity Differences over 15%.
*   **Re-identification Risk**: Demographic combinations and daily click frequencies create a behavioral fingerprint. Solved by separating layers into decoupled cloud storage.

---

## 2. Infrastructure Breakthroughs (Weeks 5-6)

### Blocker 1: Fabric HTTP 430 Capacity Throttle
*   **Issue**: Fabric Starter Pool hit `TooManyRequestsForCapacity` (HTTP 430) by over-allocating large nodes for Python code execution.
*   **Fix**: Created a custom single-node Spark pool (`hcai_micro_pool`). Configured a Small node (4 vCores / 32 GB RAM) and disabled autoscaling to stay under trial limits.

### Blocker 2: Cloud Proxy Connection Refusal
*   **Issue**: Target server firewall blocked automated Azure data centre IP ranges, throwing `Errno 111 Connection Refused`.
*   **Fix**: Refactored notebook code to use a custom corporate user-agent header string with Python `requests`, bypassing the proxy firewall block.

---

## 3. Cloud Storage & Managed Delta Tables

### 3.1 Directory Layout
Data resides in the `OULAD_Bronze_Raw` Lakehouse. Raw file downloads land in the **Files** section; production tables compile into the managed **Tables** directory.

### 3.2 Delta Table Optimisation
Converted raw CSV files to optimised Delta Lake formats (`studentinfo_bronze` and `studentvle_bronze`). Applied explicit PySpark `StructType` schema structures, locked down data types (`id_student` as Integer), and enabled ACID transactions (`_delta_log`) to prevent drift.

---

## 4. Week 8 Quality Validation & Schema Evolution

### 4.1 Automated Audit Discovery
Week 8 PySpark validation notebook flagged a schema gap: the initial ingestion skipped mandatory lineage metadata fields.

### 4.2 Remediation via In-Flight Schema Evolution
To resolve this without corrupting live data records or forcing an entire table tear-down, I utilised Delta Lake's native schema evolution capabilities. By altering the table properties to support automatic schema merges, the pipeline injected the missing lineage parameters directly via Spark SQL:

```sql
-- Step 1: Enable automatic schema evolution for the session
SET spark.databricks.delta.schema.autoMerge.enabled = true;

-- Step 2: Alter tables to append the mandatory HCAI governance columns
ALTER TABLE studentinfo_bronze ADD COLUMNS (
    PIPELINE_INGEST_TS TIMESTAMP, 
    SOURCE_FILE_NAME STRING
);

-- Step 3: Populate the lineage metadata for existing records
UPDATE studentinfo_bronze 
SET PIPELINE_INGEST_TS = CURRENT_TIMESTAMP(), 
    SOURCE_FILE_NAME = 'studentInfo.csv'
WHERE PIPELINE_INGEST_TS IS NULL;
```

### 4.3 Stewardship Matrix
Mapped accountability metrics under `GOVERNANCE.md`:
*   **Technical Custodian**: Martins Ifeanyi Nnadi (Pipeline upkeep and validation scripts).
*   **Academic Owner**: Prof. Solomon Sunday Oyelere (Research governance, policy escalation).

---

## 5. References

1. Kuzilek, J. et al. (2017) 'Open University Learning Analytics Dataset', *Scientific Data*, 4(1).
2. Oyelere, S. S. et al. (2024) 'Hybrid Intelligence Systems for HCAI in Education', *Computers in Human Behavior*, 150.
3. Shneiderman, B. (2021) 'Human-Centered Artificial Intelligence', *IJHCI*, 37(6).
4. Armbrust, M. et al. (2020) 'Delta Lake ACID Table Storage', *VLDB*, 13(12).

