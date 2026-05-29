# **OULAD Dataset Evaluation & Strategic Scoping**  
### **Framework Category:** Data Governance & Portfolio Feasibility  
### **Project Context:** Data Engineering for Human‑Centred AI Research  
### **Academic Supervisor:** Professor Solomon Sunday Oyelere  

---

## **1. Access and Licence**

### **The Baseline**  
The Open University Learning Analytics Dataset (OULAD) is publicly available via the Open University’s Knowledge Media Institute (KMi) portal [1].

### **Licensing Frame**  
The dataset is released under the **Creative Commons Attribution 4.0 International (CC BY 4.0)** license [1].

### **Governance Mapping**  
This open‑access license is ideal for public GitHub portfolios. It permits sharing, adapting, and transforming the data for research and commercial purposes, provided appropriate attribution is given to the Open University [1].

Because the dataset contains **no raw Personally Identifiable Information (PII)**—no names, emails, phone numbers, or direct identifiers—it avoids complex GDPR/HIPAA compliance barriers for sandbox experimentation.

---

## **2. Technical Richness**

### **Schema Structure**  
OULAD is not a single flat CSV. It is an **unnormalised relational schema** comprising seven interconnected tables [1]:
- `courses`  
- `assessments`  
- `vle`  
- `studentInfo`  
- `studentRegistration`  
- `studentAssessment`  
- `studentVle`

### **Scale and Diversity**  
The dataset includes **10.6M+ clickstream interaction logs** inside `studentVle`, representing real behavioural telemetry [1].

### **Engineering Opportunities**  
Working with OULAD requires:
- Multi‑table joins across relational structures
- Complex window functions for aggregating daily logs into weekly behavioural trends
- Synchronising discrete assessment events with continuous clickstream activity
- Designing scalable pipelines using Azure Fabric’s Spark/Delta engine [4]

This provides an enterprise‑grade engineering workout.

---

## **3. Research Relevance**

### **Human‑Centred Core**  
The dataset aligns strongly with Professor Oyelere’s focus on hybrid intelligence and equitable educational systems [2]. It captures real student behaviours, engagement patterns, and academic outcomes.

### **Ethical AI Grounding**  
OULAD includes protected demographic attributes [1]:
- gender  
- region (socio‑economic proxy)  
- age_band  
- disability  

This makes it a gold‑standard environment for studying **algorithmic fairness**, **predictive bias**, and **responsible AI** [3]. You can integrate tools like **Fairlearn** to ensure early‑dropout prediction models do not penalise vulnerable groups.

---

## **4. Data Quality Challenges**

Real‑world data is messy, and OULAD provides authentic engineering challenges:

### **Severe Missing Data / Null Values**  
- `date_unregistration` is sparse (only populated for dropouts).  
- `imd_band` (socio‑economic deprivation index) contains missing values.

### **Severe Class Imbalances**  
Students with disabilities represent ~10% of the dataset [1], creating underrepresentation risks that must be audited in the pipeline before modeling.

### **Asynchronous Time‑Series Alignment**  
Click logs use **relative day offsets** (e.g., Day −30 to Day 269) rather than calendar dates [1]. Your pipeline must normalise these offsets consistently.

---

## **5. Portfolio Value**

This dataset will **absolutely** demonstrate elite, highly employable data‑engineering capability. Recruiters are tired of seeing Titanic/Iris. OULAD shows you can operate at a **production‑grade level**:

### **Enterprise Architecture**  
You will implement a **Medallion Lakehouse Pattern** (Bronze → Silver → Gold) using Microsoft Fabric’s Spark/Delta engine [4].

### **Advanced Data Patterns**  
You will demonstrate:
- Handling complex relational schemas
- Transforming millions of messy log events
- Engineering analytical feature vectors at scale

### **The HCAI Premium**  
Modern organisations need engineers who understand:
- Data ethics
- Privacy engineering
- Compliance
- Bias auditing

Implementing salted SHA‑256 tokenisation, metadata lineage tracking, and Fairlearn parity checks will set your portfolio apart.

---

## **📚 References**
[1] Kuzilek, J., Hlosta, P. and Zdrahal, Z. (2017) 'Open University Learning Analytics Dataset', *Scientific Data*, 4(1), pp. 1-8. Available at: https://open.ac.uk (Accessed: 29 May 2026).  
[2] Oyelere, S. S., et al. (2024) 'A Scoping Review of Hybrid Intelligence Systems for Human-Centred AI in Education', *Computers in Human Behavior*, 150, p. 107995.  
[3] Shneiderman, B. (2021) 'Human-Centered Artificial Intelligence: Reliable, Safe & Trustworthy', *International Journal of Human–Computer Interaction*, 37(6), pp. 479-491.  
[4] Armbrust, M., et al. (2020) 'Delta Lake: High-Performance ACID Table Storage over Cloud Object Stores', *Proceedings of the VLDB Endowment*, 13(12), pp. 3411-3424.
