# ❤️ Heart Failure Prediction

[![Python](https://img.shields.io/badge/Python-3.9+-blue.svg)](https://www.python.org/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-1.0+-orange.svg)](https://scikit-learn.org/)
[![XGBoost](https://img.shields.io/badge/XGBoost-1.5+-red.svg)](https://xgboost.ai/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

## 📋 Overview

This project develops machine learning models to predict mortality in heart failure patients using clinical records. The dataset contains medical records of 299 heart failure patients collected at the Faisalabad Institute of Cardiology and Allied Hospital in Faisalabad, Pakistan.

## 🎯 Objective

To build an accurate predictive model that can identify heart failure patients at high risk of mortality, enabling healthcare providers to prioritize care and potentially save lives through early intervention.

## 📊 Dataset

The dataset contains **299 patient records** with **13 clinical features**:

| Feature | Description | Type |
|---------|-------------|------|
| age | Patient's age (years) | Numeric |
| anaemia | Decrease in red blood cells (0 = No, 1 = Yes) | Binary |
| creatinine_phosphokinase | Level of CPK enzyme in blood (mcg/L) | Numeric |
| diabetes | Presence of diabetes (0 = No, 1 = Yes) | Binary |
| ejection_fraction | Percentage of blood leaving heart per contraction | Numeric |
| high_blood_pressure | Hypertension (0 = No, 1 = Yes) | Binary |
| platelets | Platelet count in blood (kiloplatelets/mL) | Numeric |
| serum_creatinine | Creatinine level in blood (mg/dL) | Numeric |
| serum_sodium | Sodium level in blood (mEq/L) | Numeric |
| sex | Gender (0 = Female, 1 = Male) | Binary |
| smoking | Smoking status (0 = No, 1 = Yes) | Binary |
| time | Follow-up period (days) | Numeric |
| DEATH_EVENT | Target variable (0 = Survived, 1 = Died) | Binary |

### Class Distribution
- **Survived**: 203 patients (67.9%)
- **Died**: 96 patients (32.1%)

> ⚠️ **Note**: The dataset is imbalanced, which was considered during model evaluation.

## 🔍 Exploratory Data Analysis (EDA)

### Key Insights:

1. **Age Distribution**: Most patients are between 50-70 years old
2. **Age Impact**: Mortality rate is higher among patients aged 50+
3. **Diabetes**: Most diabetic patients in the dataset survived
4. **Feature Correlations**:
   - Strong negative correlation: `time` ↔ `DEATH_EVENT` (-0.53)
   - Moderate positive correlation: `serum_creatinine` ↔ `DEATH_EVENT` (0.29)
   - Moderate negative correlation: `ejection_fraction` ↔ `DEATH_EVENT` (-0.27)

## 🧠 Models Implemented

| Model | Accuracy | Precision | Recall | Confusion Matrix |
|-------|----------|-----------|--------|------------------|
| Logistic Regression (baseline) | 78.9% | 76.5% | 46.4% | [[58,4], [15,13]] |
| Logistic Regression (scaled) | 81.1% | 78.9% | 53.6% | [[58,4], [13,15]] |
| SVM | 67.8% | 40.0% | 7.1% | [[59,3], [26,2]] |
| Decision Tree | 81.1% | 72.0% | 64.3% | [[55,7], [10,18]] |
| Random Forest | **86.7%** | **90.0%** | 64.3% | [[60,2], [10,18]] |
| XGBoost | 85.6% | 80.0% | **71.4%** | [[57,5], [8,20]] |
| Gradient Boosting | 85.6% | 85.7% | 64.3% | [[59,3], [10,18]] |

### 🏆 Best Model: XGBoost

**Selected for deployment** due to:
- Highest recall (71.4%) - better at identifying patients at risk
- Strong overall accuracy (85.6%)
- Excellent handling of class imbalance
- Feature importance interpretability

## 📈 Feature Importance (XGBoost)

Top predictors for mortality:
1. **Time** - Most important predictor (longer follow-up = lower risk)
2. **Serum Creatinine** - Key kidney function indicator
3. **Age** - Higher age associated with increased risk
4. **Ejection Fraction** - Heart pumping efficiency
5. **Serum Sodium** - Electrolyte balance

## 🛠️ Technologies Used
