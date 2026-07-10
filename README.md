🛠️ Airflow 3.3 Databricks ETL Pipeline
A production-style ETL orchestration project built using Apache Airflow 3.3, Docker, and Databricks.

The pipeline orchestrates a Bronze → Silver → Validation → Gold data workflow using the TaskFlow API and Databricks Jobs.

🚀 Core Engineering Features
This project demonstrates production-oriented Airflow concepts including:

💻 TaskFlow API – Clean, pythonic DAG definitions using decorators.

☁️ Databricks Job Orchestration – Triggering and monitoring remote cloud compute clusters.

🔀 Dynamic Branching – Conditional execution paths based on operational data validation results.

🐳 Dockerized Environment – Fully isolated container setup optimized for Airflow 3.3.

🗄️ PostgreSQL Metadata Database – Persistent storage backend for workflow states and tracking.

⚡ Redis + CeleryExecutor – Scalable distributed task queue processing handling heavy concurrent workloads.

🐙 Git Version Control – Production-ready repository structure maintaining strict environment tracking.


<!-- ===============================================================================
     ============================== SECTION 1 ======================================
     =============================================================================== -->

                     Section 2  Architecture


               ┌─────────────────────────────────┐
               │    Airflow 3.3 Orchestrator     │
               └────────────────┬────────────────┘
                                │
                                ▼
               ┌─────────────────────────────────┐
               │    Databricks Jobs API Call     │
               └────────────────┬────────────────┘
                                │
                                ▼
               ┌─────────────────────────────────┐
               │          Bronze Layer           │
               │       (Raw Ingestion/CSV)       │
               └────────────────┬────────────────┘
                                │
                                ▼
               ┌─────────────────────────────────┐
               │          Silver Layer           │
               │      (Cleaned / Parquet)        │
               └────────────────┬────────────────┘
                                │
                                ▼
               ┌─────────────────────────────────┐
               │     Data Quality Validation     │
               └──────┬────────────────────┬─────┘
                      │                    │
               [PASS] │                    │ [FAIL]
                      ▼                    ▼
       ┌───────────────────────────┐  ┌───────────────────────────┐
       │        Gold Layer         │  │     Pipeline Stopped      │
       │  (Business Views / Delta) │  │   (Alert Notification)    │
       └───────────────────────────┘  └───────────────────────────┘


       <!-- ===============================================================================
     ============================== SECTION 2 ======================================
     =============================================================================== -->


                                🛠️ Tech Stack & Architecture Mapping
                        | Technology            | Purpose |
                        |------------           |---------|
                        | Apache Airflow 3.3    | Workflow Orchestration |
                        | Docker                | Containerization |
                        | Docker Compose        | Multi-container Deployment |
                        | Databricks            | Spark Processing |
                        | Delta Lake            | Storage Format |
                        | PostgreSQL            | Airflow Metadata Database |
                        | Redis                 | Celery Message Broker |
                        | Python                | DAG Development |