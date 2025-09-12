# EHR_dataset_covid19data_analysis

## 🧹 COVID-19 Healthcare Data Cleaning Pipeline  

### 📋 Overview  
This project implements a **comprehensive data cleaning and preprocessing pipeline** for the **Synthea COVID-19 dataset**.  

The workflow transforms **30M+ raw healthcare records** into an **analysis-ready dataset of 22M+ records**, specifically focused on **COVID-19 patients**.  

The pipeline ensures **high-quality, standardized, and reproducible data** suitable for:  
- Epidemiological studies  
- Healthcare utilization analysis  
- Machine learning applications  

---

## 🎯 Objectives  
- Create a COVID-19 patient cohort using **SNOMED code 840539006**  
- Improve data quality (duplicates, missing values, inconsistent formats)  
- Standardize dates, text, and categorical variables  
- Engineer clinical and analytical features for downstream research  
- Maintain referential integrity across all healthcare tables  

---

## 📊 Dataset Description  

**Source:** Synthea synthetic healthcare dataset (COVID-19 subset)  

- **Patient Population:** 124,150 COVID-19 patients  
  - Living: 100,000 (**80.5%**)  
  - Deceased: 24,150 (**19.5%**)  
- **Tables Processed:** 9 healthcare domains  
- **Records:** ~30M raw → ~22M cleaned  

---

### Processed Tables  

| Table            | Description                  | Original Records | Cleaned Records | Key Columns                       |
|------------------|------------------------------|------------------|-----------------|-----------------------------------|
| `patients_df`    | Demographics & identifiers  | 124,150          | 124,150         | Id, BIRTHDATE, DEATHDATE          |
| `conditions_df`  | Diagnoses & history         | 1,143,900        | 936,075         | START, STOP, CODE                 |
| `observations_df`| Clinical measurements       | 16,219,969       | 14,378,428      | DATE, VALUE, UNITS                |
| `encounters_df`  | Healthcare visits           | 3,188,675        | 1,975,394       | START, STOP, COST                 |
| `medications_df` | Prescriptions               | 4,227,000+       | 2,500,000+      | START, STOP, CODE                 |
| `procedures_df`  | Medical procedures          | 979,564          | 795,804         | DATE, CODE, COST                  |
| `careplans_df`   | Care and treatment plans    | 377,726          | 291,246         | START, STOP, DESCRIPTION          |
| `supplies_df`    | Medical supplies            | 1,389,858        | 1,389,786       | DATE, QUANTITY                    |
| `devices_df`     | Medical devices             | 23,694           | 18,557          | START, STOP, DESCRIPTION          |

---

## 🔧 Data Cleaning Pipeline  

**8-Step Process**  

1. **Data Loading** → 9 CSVs, 30M+ records  
2. **COVID-19 Filtering** → Select patients with SNOMED `840539006`  
3. **Duplicate Removal** → 5,723 eliminated (100% deduplication)  
4. **Missing Value Treatment** → 5.3M → 100K missing cells (**98% reduction**)  
5. **Date Standardization** → Converted to pandas datetime  
6. **Text Normalization** → Unified categorical variables  
7. **Feature Engineering** → `IS_DEAD`, `IS_ONGOING`, `AGE`, healthcare cost totals  
8. **Outlier Detection** → IQR & Z-score methods for validation  

---

## 🏥 Feature Engineering  

- **Mortality Tracking:** `IS_DEAD` flag (**19.5% deceased**)  
- **Treatment Status:** `IS_ONGOING` for active conditions/medications  
- **Patient Metrics:** `AGE`, encounter counts, healthcare costs  
- **Clinical Measures:** Length of stay, utilization patterns  

---

## ✅ Quality Improvements  

- **Duplicates:** 100% removed  
- **Missing Data:** Reduced from 5.3M → 100K cells (**98% reduction**)  
- **Date Formats:** Fully standardized  
- **Categorical Data:** Normalized across tables  
- **Integrity:** Referential links preserved  

---

## 📈 Analysis-Ready Capabilities  

The cleaned dataset supports:  
- Epidemiological analysis of COVID-19 outcomes  
- Healthcare utilization and cost studies  
- Clinical research on treatment effectiveness  
- Machine learning models for prediction  

---

## ⚙️ Technical Implementation  

- **Environment:** Jupyter Notebook + Pandas  
- **Dependencies:** `pandas`, `numpy`, `scipy`, `matplotlib`, `seaborn`  
- **Optimizations:** Memory-efficient data types, chunked loading  
- **Error Handling:** Validation checks across tables  


