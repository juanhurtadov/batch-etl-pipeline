# batch-etl-pipeline
DE project

# Batch ETL Pipeline (Airflow + PySpark + Snowflake)

## Overview
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

## Architecture

          Airflow DAG
              │
      ┌───────┴────────┐
      │                │
      Extract Task     Transform Task (Spark)
      │                │
      └───────┬────────┘
              ▼
         Load Task
              │
        Snowflake Table

## Repository Structure

```text
batch-etl-pipeline/
│
├── dags/
│   └── batch_etl_dag.py
│
├── spark_jobs/
│   ├── extract_data.py
│   └── transform_data.py
│
├── sql/
│   ├── create_tables.sql
│   └── load_to_snowflake.sql
│
├── config/
│   ├── airflow_variables.json
│   └── snowflake_config.json
│
├── data/
│   ├── raw/
│   └── processed/
│
├── notebooks/
│   └── eda.ipynb
│
├── docker/
│   ├── Dockerfile
│   └── docker-compose.yml
│
└── README.md
```

## Tech Stack

- **Airflow** — Scheduling, orchestration  
- **PySpark** — Scalable transformations  
- **Snowflake** — Cloud data warehouse  
- **Docker** — Local Airflow environment  
- **Python / SQL**  
