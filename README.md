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

flowchart TD
    A[Airflow DAG] --> B[Extract Task]
    A --> C[Transform Task (Spark)]
    B --> D[Load Task]
    C --> D
    D --> E[Snowflake Table]

## 📁 Repository Structure

batch-etl-pipeline/
├── dags/
├── spark_jobs/
├── sql/
├── config/
├── data/
├── notebooks/
├── docker/
└── README.md

## 🔧 Tech Stack

- **Airflow** — Scheduling, orchestration  
- **PySpark** — Scalable transformations  
- **Snowflake** — Cloud data warehouse  
- **Docker** — Local Airflow environment  
- **Python / SQL**  
