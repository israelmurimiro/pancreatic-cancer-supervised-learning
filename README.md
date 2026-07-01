# Supervised Learning Analysis of Urinary Biomarkers for Pancreatic Cancer

## Project Overview
This project applies supervised machine learning methods to the Debernardi et al. (2020) urinary biomarker dataset to predict pancreatic cancer diagnosis from non-invasive urinary biomarkers and demographic variables.

## Dataset
The dataset contains 590 patients with measurements of four urinary biomarkers (creatinine, LYVE1, REG1B, TFF1), age, sex, and diagnosis (healthy, benign pancreatic condition, or pancreatic ductal adenocarcinoma). Source: Debernardi et al., PLOS Medicine, 2020.

## Methods
- Data preprocessing: outlier correction, log transformation, standardisation
- Baseline models: dummy classifier, multinomial logistic regression
- Regularised regression: LASSO with cross-validation
- Generative classifiers: LDA, QDA, Naive Bayes
- Tree-based methods: single CART with cost-complexity pruning, Random Forest, XGBoost with two-stage tuning
- Support vector machine with RBF kernel
- Model evaluation: confusion matrices, ROC curves, AUC, per-class metrics
- Model interpretation: odds ratios, variable importance, SHAP values
- Subgroup analysis by sex and age
- Benchmarking against plasma CA19-9 (where available)

## Key Findings
- XGBoost achieved the highest test accuracy (62.5%) with strong PDAC detection (76.7% recall)
- LYVE1 was the dominant predictor across all models
- Tree-based ensembles outperformed linear models, confirming non-linear biomarker relationships
- Substantial sex disparity: 76.2% accuracy for females vs 50.0% for males

## R Packages Required
nnet, glmnet, MASS, e1071, randomForest, xgboost, rpart, pROC, caret

## How to Run
Open `supervised_analysis.Rmd` in RStudio and knit to PDF or HTML.