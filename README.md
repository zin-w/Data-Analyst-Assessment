# Healthcare Data Analysis and Predictive Modeling

## Overview
This project performs an end-to-end **healthcare data analysis** using Python. It involves data cleaning, exploratory data analysis (EDA), statistical testing, and predictive modeling to understand the factors influencing **the number of treatments** across various diagnosis groups, client types, and demographics.

The dataset contains over **35,000 records** of healthcare cases, including patient demographics, diagnosis information, treatment counts, and case status.

---

## Objectives
1. **Clean and prepare**; the dataset for analysis.
2. **Explore patterns**; in treatment distribution, age demographics, and client categories.
3. **Identify relationships**; between variables such as diagnosis group, age group, and case status.
4. **Perform statistical hypothesis testing**; (t-test, ANOVA, chi-square).
5. **Build and evaluate a predictive model**; to estimate the number of treatments based on available features.

---

## Data Preparation
- Removed rows with missing essential values.
- Converted date columns to datetime format.
- Created additional derived columns:
  - `Month` (for time series analysis)
- Encoded categorical variables for modeling.

---

## Exploratory Data Analysis (EDA)
### Key Insights:
- The **average patient age** was around **37.8 years**.
- Most patients received **1–2 treatments**, but some cases required up to **42 treatments**.
- The **top diagnosis groups** were:
  - Accidents and Injuries  
  - Infections  
  - Respiratory Diseases  

### Visual Analyses:
- Distribution of **age groups**, **diagnosis groups**, and **client categories**.  
- **Time series plots** of average treatments over months.  
- **Geographic and client-level summaries** comparing outcomes and treatment frequency.

---

## Statistical Analyses
### 1. **Independent Samples t-Test**
Compared treatment counts between diagnosis groups (e.g., *Cardiovascular Diseases* vs *Ear Diseases*).  
**Result:**  
- Significant difference (p < 0.001), meaning patients with cardiovascular diseases typically received more treatments than those with ear-related conditions.

### 2. **ANOVA**
Tested whether treatment counts differed significantly across all diagnosis groups.  
**Result:**  
- F(18, N) = 151.61, p < 0.001  
- Significant variation, confirming that diagnosis type influences treatment frequency.

### 3. **Pairwise t-Tests**
Conducted all group combinations with Holm correction for multiple testing.  
**Result:**  
- Many significant differences observed between major diagnostic categories.

### 4. **Chi-Square Test**
Tested association between **Age Group** and **Case Status (Active/Resolved)**.  
**Result:**  
- χ²(38) = 3514.53, p < 0.001  
- Strong relationship — older patients are more likely to have unresolved cases.

---

## Predictive Modeling
A **Random Forest Regressor** was built to predict the **Number of Treatments** using:
- `Age`
- `Diagnosis Group`
- `Client Group`
- `Status`
- `Case Country`

### Model Evaluation:
| Metric | Value |
|--------|--------|
| Mean Absolute Error (MAE) | 0.87 |
| Root Mean Squared Error (RMSE) | 1.70 |
| R² Score | 0.014 |

**Interpretation:**  
The model’s predictions deviate by less than 2 sessions on average, but it explains almost none of the variance (low R²).  
This suggests that the selected features are insufficient to predict treatment counts — unobserved factors like disease severity, treatment protocols, and physician decisions likely play larger roles.

---

## Tools & Libraries
- **Python**
- **Pandas**, **NumPy**
- **Matplotlib**, **Seaborn**
- **SciPy**, **Statsmodels**
- **Scikit-learn**

