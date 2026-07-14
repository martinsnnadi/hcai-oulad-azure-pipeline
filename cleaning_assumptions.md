# OULAD Silver Cleaning Assumptions Log

**Track**: Week 9 Education Conformance
**Lakehouse**: OULAD_DENG_Silver_Audited

---

### 1. Identifier Standardization
*   **Assumption**: Student IDs (`id_student`) and site resource codes (`id_site`) must be integers for optimal index performance.
*   **Action**: Cast both fields to IntegerType. Filtered out any records missing structural IDs to prevent relational join breaks.

### 2. Null Treatment & Text Cleanup
*   **Assumption**: Blank entries in the Index of Multiple Deprivation (`imd_band`) represent unrecorded regional data. Leaving them empty skews profiling metrics.
*   **Action**: Converted empty values to an explicit `"Unknown"` string marker. Applied `F.trim()` to all text variables (`gender`, `region`, `highest_education`) to strip leading/trailing spaces and block duplicate categories.

### 3. Clickstream Volume Constraints
*   **Assumption**: Click entries with `sum_click <= 0` or negative values are system logging errors, not true student learning interactions.
*   **Action**: Enforced a strict positive filter (`daily_click_count > 0`) to keep only legitimate interaction signals.

### 4. Storage Architecture
*   **Assumption**: Querying raw loose files inside the operational layer slows compute performance.
*   **Action**: Converted all loose tables into optimized, managed Delta Lake tables inside the `OULAD_DENG_Silver_Audited` Lakehouse workspace.
