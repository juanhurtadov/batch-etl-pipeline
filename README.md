# batch-etl-pipeline
DE project

# Batch ETL Pipeline (Airflow + PySpark + Snowflake)

## 🚀 Overview
This project implements a production-style Batch ETL pipeline using:

- **Apache Airflow** for orchestration  
- **PySpark** for distributed data transformations  
- **Snowflake** as the cloud data warehouse  

The pipeline runs daily and performs:

1. **Extract**  
   - Downloads raw CSV/API data  
   - Stores it in `data/raw/`

2. **Transform**  
   - Cleans schema using PySpark  
   - Validates column types  
   - Handles missing values  
   - Writes processed files to `data/processed/`

3. **Load**  
   - Uploads processed data into Snowflake  
   - Uses Snowflake connector for Python or Spark connector  

---

## 🧱 Architecture

      Airflow DAG
          │
  ┌───────┴────────┐
  │                │
Extract Task Transform Task (Spark)