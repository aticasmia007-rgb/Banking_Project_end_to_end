# End-to-End Banking Big Data Pipeline

This repository contains the implementation of an end-to-end banking data pipeline using the **Medallion Architecture (Bronze, Silver, Gold)** in **Databricks**, orchestrated with **Databricks Workflows**, audited using **Great Expectations**, and visualized in **Power BI (DirectQuery)**.

---

## Pipeline Architecture

1. **Bronze (Raw Ingestion):** SQL ingestion of raw data, data type casting, defensive null handling, and deduplication.
2. **Silver (Data Modeling & Privacy):** PII anonymization using the **SHA2** algorithm and **Star Schema** modeling (`dim_customers`, `dim_accounts`, `dim_date`, `fact_transactions`).
3. **Gold (Analytics & Data Quality):** Automated data auditing with **Great Expectations (GX 1.0+)** and custom PySpark validation rules prior to BI consumption.

---

## Orchestration (Databricks Workflows)

The pipeline executes the following notebooks in sequence:
`01_bronze_Ingestion` ➡️ 
`02_to_Bronze` ➡️
 `03_Bronze_to_Silver` ➡️ `04_Silver_to_Gold_modeling` ➡️ `05_Data_Quality_Check` ➡️ 
 `05.1_Data_Great_Expectations` ➡️ `06_Gold_Analytics_Report`

> *The complete Job definition is exported as a JSON file at `workflows/banking_pipeline_job.json`.*

---

## Tech Stack

- **Processing & Compute:** Databricks (PySpark, SQL)
- **Data Governance & Quality:** Great Expectations (Fluent API 1.0+)
- **Visualization:** Power BI (DirectQuery mode)
- **Version Control:** GitHub + Databricks Git Folders