---

# 🧬 Pancreatic Cancer Biomarker Analysis

## 🎯 Overview

This project leverages a dataset of urinary biomarkers to develop a diagnostic framework for identifying **Pancreatic Ductal Adenocarcinoma (PDAC)**. Given that pancreatic cancer has a notoriously low five-year survival rate, developing non-invasive, accessible screening methods is a critical medical challenge.

---

## 📂 Repository Structure

The project is structured to ensure a reproducible pipeline from raw data to final analysis:

```text
├── README.md               # Project overview, methodology, and findings
├── data/
│   └── Debernardi et al 2020 data.csv  # Raw clinical dataset
├── supervised_analysis.Rmd # Full analysis pipeline code
├── supervised_analysis.pdf # Compiled report of the statistical analysis
└── .gitignore              # Files to exclude from version control

```

---

## 🛠️ Methodology Highlights

The analytical pipeline, detailed in `supervised_analysis.Rmd`, includes the following core steps:

* **Data Cleaning:** We addressed typographical errors in creatinine and LYVE1 and determined that an extreme TFF1 value was a legitimate physiological signal.
* **Preprocessing:** To handle significant right-skewness, we applied **log transformations** to LYVE1, REG1B, and TFF1.
* **Standardization:** All continuous predictors were standardized (mean = 0, unit variance = 1) to ensure equal contribution to the models.
* **Site Effect Mitigation:** **ANOVA** testing confirmed systematic site-specific variations (batch effects); consequently, collection origin was excluded as a predictor to prevent the model from learning site-specific technical noise rather than biological signals.

---

## 🩺 Clinical Implications & Feature Analysis

* **Screening Potential:** The model achieved 76.7% recall for PDAC detection, suggesting utility as a screening tool to flag high-risk individuals.
* **Accessible Diagnostics:** Urine-based collection enables low-cost, accessible screening that could be deployed in primary care settings where blood draws or imaging are impractical.
* **Risk Stratification:** Given modest overall accuracy, the model is best used as a risk-scoring tool for referral rather than a definitive diagnostic test.
* **Simplified Panels:** The dominance of **LYVE1** in all models suggests that a simplified screening panel focusing on this single urinary protein, combined with age, may provide comparable performance to the full four-biomarker set.
* **XGBoost Insight:** We analyzed the **feature importance metrics** for the XGBoost model, which consistently prioritized LYVE1 and TFF1 as the strongest predictors of malignancy, reinforcing their value for future diagnostic panels.
* **Future Validation:** All findings require validation in an independent, prospectively collected cohort to address sex disparities and site-specific effects before clinical translation.

---

## 📊 Supplementary Binary Analysis

When Benign cases are reclassified as "Non-Sick" and PDAC as "Sick," the binary accuracy improves significantly, confirming that the panel captures a strong malignant-versus-non-malignant clinical signal.

| Model | Binary Accuracy |
| --- | --- |
| **Random Forest** | **83.0%** |
| **XGBoost** | **83.0%** |
| SVM | 80.7% |
| LASSO | 78.4% |
| Logistic Regression | 77.3% |
| Dummy Baseline | 65.9% |

---
