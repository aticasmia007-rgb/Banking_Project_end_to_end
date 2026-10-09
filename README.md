# End-to-End Banking Big Data Pipeline

This repository contains the implementation of an end-to-end banking data pipeline using the **Medallion Architecture (Bronze, Silver, Gold)** in **Databricks**, orchestrated with **Databricks Workflows**, audited using **Great Expectations**, and visualized in **Power BI (DirectQuery)**.

<img width="947" alt="dashboard_bank" src="https://github.com/user-attachments/assets/6a59d083-2482-47d5-abf3-2f95eb34059b" />

---

## Pipeline Architecture

1. **Bronze (Raw Ingestion):** SQL ingestion of raw data, data type casting, defensive null handling, and deduplication.
2. **Silver (Data Modeling & Privacy):** PII anonymization using the **SHA2** algorithm and **Star Schema** modeling (`dim_customers`, `dim_accounts`, `dim_date`, `fact_transactions`).
3. **Gold (Analytics & Data Quality):** Automated data auditing with **Great Expectations (GX 1.0+)** and custom PySpark validation rules prior to BI consumption.

### Dimensional Data Model (Star Schema)
<img width="754" alt="star_schema" src="https://github.com/user-attachments/assets/940ec936-5f40-4fe6-a909-5d4f05e3999d" />

### Data Quality & Validation (Great Expectations)
<img width="900" alt="success_Great_Expectations" src="https://github.com/user-attachments/assets/4560ba56-cbd6-426f-a1e9-927fac69aefb" />

---

## Orchestration (Databricks Workflows)

The pipeline executes the following notebooks in sequence:
`01_bronze_Ingestion` ➡️ `02_to_Bronze` ➡️ `03_Bronze_to_Silver` ➡️ `04_Silver_to_Gold_modeling` ➡️ `05_Data_Quality_Check` ➡️ `05.1_Data_Great_Expectations` ➡️ `06_Gold_Analytics_Report`

> *The complete Job definition is exported as a JSON file at `workflows/banking_pipeline_job.json`.*

<img width="1459" alt="workflow_schema" src="https://github.com/user-attachments/assets/c23c2a8c-63dd-4b21-a4d2-4e8e86a18b05" />

---

## Tech Stack

- **Processing & Compute:** Databricks (PySpark, SQL)
- **Data Governance & Quality:** Great Expectations (Fluent API 1.0+)
- **Visualization:** Power BI (DirectQuery mode)
- **Version Control:** GitHub + Databricks Git Folders
