# 🚀 AdventureWorks Data Engineering Pipeline

<p align="center">

![Python](https://img.shields.io/badge/Python-blue?style=for-the-badge&logo=python)
![Apache Airflow](https://img.shields.io/badge/Apache%20Airflow-green?style=for-the-badge&logo=apacheairflow)
![Databricks](https://img.shields.io/badge/Databricks-Lakehouse-orange?style=for-the-badge&logo=databricks)
![Apache Spark](https://img.shields.io/badge/Apache%20Spark-PySpark-E25A1C?style=for-the-badge&logo=apachespark)
![Delta Lake](https://img.shields.io/badge/Delta%20Lake-Storage-blue?style=for-the-badge)
![AWS S3](https://img.shields.io/badge/AWS-S3-FF9900?style=for-the-badge&logo=amazonaws)
![Power BI](https://img.shields.io/badge/Power%20BI-Dashboard-F2C811?style=for-the-badge&logo=powerbi)
![Docker](https://img.shields.io/badge/Docker-Container-2496ED?style=for-the-badge&logo=docker)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-CI/CD-2088FF?style=for-the-badge&logo=githubactions)

</p>

---

# 📖 About This Project

This repository contains my first end-to-end Data Engineering project.

I built this project to understand how a modern batch data pipeline works in a real-world environment. Instead of learning each tool separately, I wanted to connect everything together—from data ingestion to reporting.

The project starts by extracting data from AdventureWorks platform and convert them into csv and load them into S3 and second fase was reading raw AdventureWorks data from AWS S3. Apache Airflow orchestrates the pipeline, Databricks processes the data using PySpark, Delta Lake stores each Medallion layer, and the final Gold tables are used to build Power BI dashboards.

While building this project, my goal wasn't just to make the pipeline work. I wanted to learn how different components work together, how data flows through each layer, and how Data Engineers design reliable and maintainable pipelines.

This project covers:

- End-to-end ETL/ELT pipeline
- Medallion Architecture (Bronze, Silver, Validation, Gold)
- Apache Airflow orchestration
- Databricks Workflows
- Delta Lake MERGE operations
- Incremental data processing
- Data quality validation
- Star Schema data modeling
- Databricks SQL Warehouse
- Power BI dashboards
- Dockerized Airflow
- GitHub Actions CI

Although this is a portfolio project, I tried to follow production-inspired practices wherever possible and document the design decisions throughout the repository.

---

# 🎯 Why I Built This

I created this project to challenge myself with a complete Data Engineering workflow instead of building small isolated examples.

During this project I learned how data moves through a modern data platform, how orchestration works, how Delta Lake handles incremental data, how to model analytical data, and how to deliver business-ready datasets for reporting.

More importantly, I learned how to debug failures, improve pipeline design, and think about Data Engineering beyond writing code.

---

# 🙌 Feedback Welcome

This is my **first Data Engineering project**, and I'm still learning.

If you notice something that could be improved, an engineering decision that could be better, or a practice that isn't production-ready, I'd genuinely appreciate your feedback.

Constructive criticism helps me become a better Data Engineer, and I'd much rather learn by fixing mistakes than leave them unnoticed.

If you have suggestions, advice, or would simply like to connect and discuss Data Engineering, feel free to reach out to me on **LinkedIn**.

I'm always open to learning from experienced engineers and improving my work.

# 🏗️ Project Architecture

One of the main goals of this project was to understand how data moves through a complete Data Engineering pipeline. Instead of processing everything in a single script, I followed the Medallion Architecture to organize the data into different layers, making the pipeline easier to maintain, debug, and scale.

The pipeline starts when raw AdventureWorks CSV files are uploaded to an AWS S3 bucket. Apache Airflow monitors and orchestrates the workflow, while Databricks Workflows execute the PySpark notebooks responsible for processing each layer of the pipeline.

Each layer has a specific responsibility:

### 🥉 Bronze Layer

The Bronze layer stores the raw source data exactly as it arrives from Amazon S3.

At this stage I don't perform any business transformations. The main goal is to preserve the original data so it can always be traced back if something goes wrong later in the pipeline.

I also add ingestion metadata such as processing timestamps and a `pipeline_run_id` that allows the pipeline to process data incrementally.

---

### 🥈 Silver Layer

The Silver layer is where the data starts becoming useful.

In this layer I clean inconsistent values, standardize data types, remove duplicates, and apply business transformations using PySpark.

Instead of rewriting the entire dataset every time, I use Delta Lake MERGE operations to perform incremental updates based on the current pipeline run.

---

### ✅ Validation Layer

Before publishing data to the Gold layer, I run a separate validation step.

The purpose of this layer is to detect common data quality issues before they reach the reporting layer.

Some of the validations include:

- Checking for null values in important columns
- Verifying numeric values are valid
- Detecting duplicate records
- Logging validation results for every pipeline execution

Separating validation from transformation makes the pipeline easier to troubleshoot and helps identify data quality issues earlier.

---

### 🥇 Gold Layer

The Gold layer contains business-ready tables designed for reporting and analytics.

Here I build a Star Schema consisting of fact and dimension tables.

These tables are optimized for business users and Power BI dashboards instead of raw data processing.

The final Gold tables are published through Databricks SQL Warehouse, allowing Power BI to connect directly to curated analytical data.

---

# 🔄 End-to-End Pipeline Flow

The complete workflow follows the architecture below.

```text
AdventureWorks CSV Files
            │
            ▼
        AWS S3 Bucket
            │
            ▼
    Apache Airflow DAG
            │
            ▼
  Databricks Workflow
            │
            ▼
     Bronze Layer
            │
            ▼
     Silver Layer
            │
            ▼
   Data Validation
            │
            ▼
      Gold Layer
            │
            ▼
 Databricks SQL Warehouse
            │
            ▼
        Power BI
```

This separation allows each layer to have a single responsibility, making the pipeline easier to maintain and extend in the future.

---

# ⚡ Incremental Processing

One thing I wanted to avoid was reprocessing the entire dataset every time the pipeline runs.

To solve this, I implemented incremental processing using a unique `pipeline_run_id`.

Each pipeline execution processes only the newly ingested records, which are then merged into Delta Lake tables using MERGE operations.

This approach reduces unnecessary processing while keeping the data up to date.

---

# 🛠️ Technologies Used

This project helped me gain hands-on experience with several tools commonly used in modern Data Engineering.

| Tool | Purpose |
|------|---------|
| Python | Pipeline development |
| PySpark | Distributed data processing |
| Apache Airflow | Workflow orchestration |
| Databricks Workflows | Notebook execution |
| Delta Lake | ACID storage & incremental MERGE |
| AWS S3 | Raw data storage |
| Unity Catalog | Table management |
| Databricks SQL Warehouse | SQL endpoint for reporting |
| Power BI | Dashboard creation |
| Docker | Local Airflow environment |
| GitHub Actions | Continuous Integration |

---

# 💡 What I Learned

This project taught me much more than how to write PySpark code.

Some of my biggest takeaways were:

- Breaking a large pipeline into small, maintainable layers.
- Understanding why orchestration is just as important as transformation.
- Designing incremental pipelines instead of full refresh pipelines.
- Building a dimensional model for analytics.
- Thinking about data quality before reporting.
- Using GitHub Actions to automatically validate changes.
- Documenting architecture instead of only writing code.

Building this project helped me understand how different Data Engineering tools work together to solve a complete business problem instead of learning them in isolation.
