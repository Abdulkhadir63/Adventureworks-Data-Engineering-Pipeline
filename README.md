# 🚀 AdventureWorks Data Engineering Pipeline

<p align="center">

![Python](https://img.shields.io/badge/Python-blue?style=for-the-badge&logo=python)
![Apache Airflow](https://img.shields.io/badge/Apache%20Airflow-red?style=for-the-badge&logo=apacheairflow)
![Databricks](https://img.shields.io/badge/Databricks-Lakehouse-orange?style=for-the-badge&logo=databricks)
![Apache Spark](https://img.shields.io/badge/Apache%20Spark-PySpark-E25A1C?style=for-the-badge&logo=apachespark)
![Delta Lake](https://img.shields.io/badge/Delta%20Lake-Storage-blue?style=for-the-badge)
![AWS S3](https://img.shields.io/badge/AWS-S3-FF9900?style=for-the-badge&logo=amazonaws)
![Power BI](https://img.shields.io/badge/Power%20BI-Dashboard-F2C811?style=for-the-badge&logo=powerbi)
![Docker](https://img.shields.io/badge/Docker-Container-2496ED?style=for-the-badge&logo=docker)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-CI/CD-2088FF?style=for-the-badge&logo=githubactions)

</p>

---

# 📖 Project Overview

This project demonstrates a production-inspired end-to-end Data Engineering pipeline built using the AdventureWorks dataset. The pipeline follows the Medallion Architecture (Bronze → Silver → Validation → Gold) to ingest, transform, validate, and model business data for analytics and reporting.

The primary objective of this project is to simulate how modern Data Engineering teams build scalable and reliable batch data pipelines using industry-standard tools and best practices.

The solution combines Apache Airflow for orchestration, Databricks for distributed data processing, Delta Lake for reliable storage and ACID transactions, AWS S3 as the data lake, and Power BI for business intelligence.

Rather than focusing only on data transformation, this project demonstrates the complete engineering lifecycle, including orchestration, incremental processing, data quality validation, dimensional modeling, CI/CD automation, and interactive reporting.

---

# 🎯 Business Problem

Organizations receive data from multiple operational systems every day. Raw files often contain duplicate records, inconsistent formats, invalid values, and changing schemas. Without a structured data engineering process, these issues lead to unreliable reporting and poor business decisions.

To solve this challenge, this project implements a modern Lakehouse architecture that:

- Ingests raw CSV files from Amazon S3.
- Preserves raw data in the Bronze layer.
- Cleanses and standardizes data in the Silver layer.
- Performs automated data quality validation.
- Builds analytical Gold tables using a dimensional model.
- Serves curated datasets to Power BI for business reporting.

This approach separates raw ingestion from business-ready analytics while maintaining data reliability and scalability.

---

# 🏗️ Solution Architecture

The pipeline is orchestrated by Apache Airflow, which triggers Databricks Workflows to process data through each Medallion layer. Data is stored in Delta Lake tables within Unity Catalog, ensuring ACID transactions and efficient incremental processing.

The final Gold layer is exposed through Databricks SQL Warehouse, enabling Power BI to build interactive dashboards directly on curated business tables.

> 📌 **Architecture Diagram**

<p align="center">

**Replace this section with your architecture diagram image**

```text
docs/Architecture_Diagram.png
```

</p>

---

# ⚙️ Technology Stack

| Category | Technology |
|----------|------------|
| Programming Language | Python |
| Distributed Processing | Apache Spark (PySpark) |
| Orchestration | Apache Airflow |
| Workflow Execution | Databricks Workflows |
| Storage Format | Delta Lake |
| Cloud Storage | AWS S3 |
| Metadata | Unity Catalog |
| Data Modeling | Star Schema |
| BI & Visualization | Power BI |
| Version Control | Git & GitHub |
| CI/CD | GitHub Actions |
| Containerization | Docker |
| Dataset | Microsoft AdventureWorks |

---

# ⭐ Key Features

- End-to-End Medallion Architecture
- Automated Pipeline Orchestration with Apache Airflow
- Distributed Data Processing using PySpark
- Incremental Data Loading using `pipeline_run_id`
- Delta Lake MERGE (Upsert) Operations
- Automated Data Quality Validation
- Star Schema Data Warehouse Design
- Databricks SQL Warehouse Integration
- Interactive Power BI Dashboards
- Dockerized Development Environment
- GitHub Actions Continuous Integration (CI)
- Production-Oriented Repository Structure

---

# 📂 Repository Structure

```text
Adventureworks-Data-Engineering-Pipeline
│
├── dags/
│   └── adventure_work_project/
│
├── databricks/
│   ├── bronze/
│   ├── silver/
│   ├── validation/
│   └── gold/
│
├── docs/
│
├── powerbi/
│
├── .github/
│   └── workflows/
│
├── Dockerfile
├── docker-compose.yaml
├── requirements.txt
├── README.md
└── .env.example
```
