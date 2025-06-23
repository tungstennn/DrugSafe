# 💊 DrugSafe

> A data engineering pipeline that transforms real-world FDA adverse drug event data into an analyzable, trustworthy dataset for risk analysis and reporting.

---

## 📌 Project Summary

**DrugSafeAI** is a data engineering project built to ingest, clean, validate, and transform public healthcare data from the [FDA Adverse Event Reporting System (FAERS)](https://open.fda.gov/apis/drug/event/). The goal is to build an end-to-end ELT pipeline into Snowflake, applying industry-standard practices around data validation, modeling, and analytics delivery.

The focus of this project is to build a **robust, reproducible data pipeline**, aligned with the real-world expectations of data engineering roles — from ingestion to reporting.

---

## 🚨 Problem Statement

Adverse drug events are frequently reported by healthcare professionals and patients, but these reports are messy, inconsistent, and difficult to analyze.  
There is a need for a reliable pipeline that transforms raw reports into clean, structured data to support decision-making around **drug safety trends**, **high-risk populations**, and **drug-outcome relationships**.

---

## 🎯 Project Goals

- ✅ Ingest data via the openFDA Drug Event API
- ✅ Validate and clean datasets using **Great Expectations**
- ✅ Load data into **Snowflake** using efficient staging logic
- ✅ Transform into a **star schema** for analysis
- ✅ Enable dimensional exploration by patient demographics, reactions, and drug classes
- ⬜ (Optional) Explore basic machine learning for severity prediction

---

## ⚙️ Tech Stack

| Layer              | Tool / Framework         |
|--------------------|--------------------------|
| 💽 Data Warehouse   | Snowflake                |
| 🔄 Ingestion        | Python (requests, pandas)|
| 🧹 Transformation   | pandas + Snowflake SQL   |
| ✅ Validation       | Great Expectations (optional)      |
| ☁️ Orchestration    | Apache Airflow|
| 📊 Dashboard        | Tableau or Streamlit     |

---

## 🧱 Pipeline Structure

### 1. **Extract**
- Call the FDA Drug Event API to retrieve adverse event records
- Normalize nested JSON into flat, relational pandas DataFrames

### 2. **Load**
- Push raw and cleaned data into Snowflake staging tables

### 3. **Validate**
- Use **Great Expectations** to apply column-level and dataset-level checks:
  - Missing values
  - Valid ranges (e.g., age)
  - Expected value sets (e.g., gender: M/F/U)

### 4. **Transform**
- Create:
  - `fact_adverse_event`
  - `dim_patient`
  - `dim_drug`
  - `dim_reaction`
  - `dim_time`
- Apply SQL logic inside Snowflake for scalable transformation

### 5. **Serve**
- Export tables to dashboarding tools or run queries for insights

---

## 🔍 Example Questions the Data Will Answer

- Which drugs are most commonly associated with serious outcomes?
- Are older populations more likely to experience adverse effects for certain drug classes?
- How do outcomes differ by gender or reporting country?

---

## 🧠 Optional ML Module (Deferred)

While this project prioritizes DE best practices, an optional future extension includes:

- Training a basic **Logistic Regression** model on drug event data
- Predicting the severity of outcomes using features like age, sex, drug name, and reaction term
- Storing model outputs back into Snowflake for further analysis

> ⚠️ Note: This ML component is **not a priority** and is deferred until DE foundations are fully implemented.

---

## 📂 Folder Structure (Preview)

