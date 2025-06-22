# 💊 DrugSafeAI

> A machine learning-powered pipeline for predicting severe adverse drug reactions using real-world FDA data.

---

## 📌 Project Summary

**DrugSafeAI** is an end-to-end data pipeline that ingests publicly available FDA adverse event data and predicts the likelihood of severe outcomes (e.g. hospitalization, death) based on factors such as drug type, patient demographics, and reported reactions.  
The goal is to build an ML-assisted analytics layer that can surface risk patterns across populations and drug categories — making drug safety data more actionable and insightful.

---

## 🚨 Problem Statement

Millions of adverse drug reactions are reported globally each year, but they're often siloed, unstructured, and hard to interpret at scale.  
Clinicians, regulators, and patients need better tools to assess the **potential severity** of drug–patient combinations.  

**This project aims to:**
- Clean and structure real-world adverse event data
- Predict risk of severe outcomes using ML
- Enable meaningful dimensional analysis of drug safety trends

---

## ⚙️ Tech Stack

| Layer              | Tool / Framework         |
|--------------------|--------------------------|
| 💽 Data Warehouse   | Snowflake                |
| 🔄 Ingestion        | Python (requests, pandas)|
| 🧹 Transformation   | pandas, SQL              |
| ✅ Validation       | Pandera (optional)       |
| 🤖 Machine Learning | scikit-learn             |
| ☁️ Orchestration    | Apache Airflow (optional)|
| 📊 Visualization    | Streamlit / Tableau      |

---

## 🧱 Pipeline Steps

### 1. **Extract**
- Pull adverse event reports from the [FDA Drug Event API](https://open.fda.gov/apis/drug/event/)
- Store raw JSON into normalized pandas DataFrames

### 2. **Load**
- Upload cleaned data into Snowflake staging tables

### 3. **Transform**
- Derive features like:
  - Age group
  - Drug class
  - Reaction keywords
- Build a **star schema**:  
  e.g., `fact_adverse_event`, `dim_drug`, `dim_patient`, `dim_time`

### 4. **Model**
- Train a simple **Logistic Regression classifier** to predict severity:
  - **Input**: age, sex, drug name, reaction term
  - **Output**: probability of severe outcome (e.g. death, hospitalization)

### 5. **Serve**
- Store prediction results back in Snowflake
- Create visual dashboards or serve scores in a web app

---

## 🤖 ML Component (Severity Prediction)

| Feature            | Example Value     |
|--------------------|------------------|
| Patient Age        | 67               |
| Patient Sex        | Female           |
| Drug Name          | Warfarin         |
| Reaction Term      | Hemorrhage       |

**Model Output:**  
`Severity Score = 0.84` → flagged as high-risk

---

## 🔍 Potential Insights

- Which drugs are most often associated with high-severity events in the elderly?
- Are there gender-specific trends in reported drug risks?
- What’s the geographic distribution of high-risk reports?

---
