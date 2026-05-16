<!--
# **OULAD Dataset Evaluation & Strategic Scoping**  
### **Framework Category:** Data Governance & Portfolio Feasibility  
### **Project Context:** Data Engineering for Human‑Centred AI Research  

---

## **1. Access and Licence**

### **The Baseline**  
The Open University Learning Analytics Dataset (OULAD) is publicly available via the Open University’s Knowledge Media Institute (KMi) portal [1].

### **Licensing Frame**  
The dataset is released under the **Creative Commons Attribution 4.0 International (CC BY 4.0)** license.

### **Governance Mapping**  
This open‑access license is ideal for public GitHub portfolios. It permits sharing, adapting, and transforming the data for research and commercial purposes, provided appropriate attribution is given to the Open University [1].

Because the dataset contains **no raw Personally Identifiable Information (PII)**—no names, emails, phone numbers, or direct identifiers—it avoids complex GDPR/HIPAA compliance barriers for sandbox experimentation.

---

## **2. Technical Richness**

### **Schema Structure**  
OULAD is not a single flat CSV. It is an **unnormalised relational schema** comprising seven interconnected tables:

- `courses`  
- `assessments`  
- `vle`  
- `studentInfo`  
- `studentRegistration`  
- `studentAssessment`  
- `studentVle`

### **Scale and Diversity**  
The dataset includes **10.6M+ clickstream interaction logs** inside `studentVle`, representing real behavioural telemetry.

### **Engineering Opportunities**  
Working with OULAD requires:

- Multi‑table joins across relational structures  
- Complex window functions for aggregating daily logs into weekly behavioural trends  
- Synchronising discrete assessment events with continuous clickstream activity  
- Designing scalable pipelines using Azure Fabric’s Spark/Delta engine  

This provides an enterprise‑grade engineering workout.

---

## **3. Research Relevance**

### **Human‑Centred Core**  
The dataset aligns strongly with Professor Oyelere’s focus on equitable educational systems. It captures real student behaviours, engagement patterns, and academic outcomes.

### **Ethical AI Grounding**  
OULAD includes protected demographic attributes:

- gender  
- region (socio‑economic proxy)  
- age_band  
- disability  

This makes it a gold‑standard environment for studying **algorithmic fairness**, **predictive bias**, and **responsible AI**.  
You can integrate tools like **Fairlearn** to ensure early‑dropout prediction models do not penalise vulnerable groups.

---

## **4. Data Quality Challenges**

Real‑world data is messy, and OULAD provides authentic engineering challenges:

### **Severe Missing Data / Null Values**  
- `date_unregistration` is sparse (only populated for dropouts).  
- `imd_band` (socio‑economic deprivation index) contains missing values.

### **Severe Class Imbalances**  
Students with disabilities represent ~10% of the dataset, creating underrepresentation risks that must be audited.

### **Asynchronous Time‑Series Alignment**  
Click logs use **relative day offsets** (e.g., Day −30 to Day 269) rather than calendar dates.  
Your pipeline must normalise these offsets consistently.

---

## **5. Portfolio Value**

This dataset will **absolutely** demonstrate elite, highly employable data‑engineering capability.

Recruiters are tired of seeing Titanic/Iris.  
OULAD shows you can operate at a **production‑grade level**:

### **Enterprise Architecture**  
You will implement a **Medallion Lakehouse Pattern** (Bronze → Silver → Gold) using Microsoft Fabric’s Spark/Delta engine.

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

-->
