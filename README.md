---

# 🤖 Supervised Machine Learning: Pancreatic Cancer Diagnosis

This project implements a multi-model supervised learning pipeline to classify pancreatic health status based on urinary biomarkers. By comparing classical statistical models against advanced ensemble techniques, the project explores the predictive capacity of non-invasive biomarkers in distinguishing healthy, benign, and malignant pancreatic conditions.

---

## 📊 Project Overview

The study analyzes a dataset of 590 patients, leveraging four key urinary biomarkers (**LYVE1, REG1B, TFF1, Creatinine**) alongside demographic features. The core objective is to determine whether machine learning models can outperform traditional diagnostic benchmarks and provide interpretability into biomarker-driven risk profiles.

---

## 🛠️ Methodology

The analysis employs a robust pipeline to handle high-dimensional clinical data and class imbalance:

* **Preprocessing:** Log-transformation of biomarker concentrations and feature standardization to ensure model convergence.
* **Model Hierarchy:**
* **Baseline:** Dummy classifier and Multinomial Logistic Regression.
* **Regularized Regression:** LASSO for feature selection and shrinkage.
* **Generative/Probabilistic:** LDA, QDA, and Naive Bayes.
* **Advanced Ensembles:** CART (pruned), Random Forest, and two-stage tuned XGBoost.
* **Kernel Methods:** Support Vector Machines (SVM) with RBF kernels.


* **Evaluation Framework:** Multi-class performance assessment via confusion matrices, ROC/AUC metrics, and SHAP (SHapley Additive exPlanations) for model interpretability.

---

## 🔑 Key Findings

| Model | Test Accuracy | Performance Insight |
| --- | --- | --- |
| **XGBoost** | **62.5%** | Highest predictive power with superior PDAC recall (76.7%). |
| **Linear Models** | Moderate | Outperformed by ensembles, suggesting non-linear biomarker interactions. |
| **LYVE1** | Dominant | Consistently identified as the most critical feature across all models. |
| **Sex Disparity** | Significant | Higher model accuracy for females (76.2%) vs. males (50.0%). |

> **Supplementary Insight:** When simplifying the clinical question from multi-class to binary (PDAC vs. Non-PDAC), models like XGBoost and Random Forest achieved up to **83.0% accuracy**, demonstrating that the biomarkers are highly effective at identifying malignancy, even if they struggle to differentiate between benign and healthy states.

---

## 📂 Repository Structure

```text
supervised-pancreatic-analysis/
├── data/               # Processed biomarker dataset
├── R/                  # ML training scripts & model tuning pipelines
├── models/             # Saved model objects & hyperparameter configs
├── reports/            # Performance curves (ROC/AUC) & SHAP visualisations
├── supervised_analysis.Rmd # Main analysis & benchmarking document
└── requirements.R      # Project dependency list

```

---

## 🚀 How to Run

1. Ensure **R** and **RStudio** are installed.
2. Install the necessary machine learning libraries:
```r
install.packages(c("nnet", "glmnet", "MASS", "e1071", "randomForest", 
                   "xgboost", "rpart", "pROC", "caret"))

```


3. Open `supervised_analysis.Rmd` in RStudio.
4. Execute the cells to retrain the models or **Knit** to generate the final analytical report.

---

## 🧠 Model Interpretability & Bias

The analysis highlights a notable performance gap between sexes, suggesting that biomarker thresholds for PDAC may not be sex-invariant. Future iterations should explore sex-stratified thresholds or domain adaptation techniques to mitigate this bias. The use of SHAP values provides a transparent view of how each biomarker contributes to individual patient risk predictions.

---

## 👤 Author

**MURIMIRO ISRAEL** *Date: 2026-06-19*
