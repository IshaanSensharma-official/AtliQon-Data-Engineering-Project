AtliQon & SportsBar: Unified Data Engineering Pipeline

📌 Project Overview
In this project, I acted as a Data Engineer for AtliQon, a leading sports equipment manufacturer. Following the acquisition of a startup called SportsBar, the company faced a major "Data Chaos" problem: disparate formats, inconsistent metrics, and missing historical records.
I built an end-to-end ETL pipeline using the Medallion Architecture in Databricks to ingest, clean, and unify data from both companies into a single "Source of Truth" for executive decision-making.


 
🏗️ Technical Architecture
The pipeline follows a modern data lakehouse pattern, moving data through three distinct stages of refinement.
Note: While the original project used AWS S3, this implementation utilizes Databricks Volumes (Unity Catalog) as the landing zone for raw data to optimize for a native Databricks environment.
Bronze (Raw): Ingested raw CSV files from landing zones into Delta tables with minimal transformation, preserving data lineage with metadata columns (file name, load timestamp).
Silver (Cleaned): Performed data quality checks, handled null values, fixed spelling inconsistencies (e.g., "Protin" to "Protein"), and standardized date formats using PySpark.
Gold (Curated): Created business-level aggregates and joined dimension tables into a unified Star Schema for BI reporting.



🛠️ Tech Stack
Platform: Databricks (Free Edition)
Language: PySpark (Python), Spark SQL
Storage: Delta Lake (Unity Catalog Volumes)
Orchestration: Databricks Workflows (Jobs)
Visualization: Databricks SQL Dashboards



📊 Data Modeling
The project is modeled using a Star Schema, optimized for analytical performance.
Fact Table: fact_orders (Quantity, Revenue metrics)
Dimension Tables: * dim_customers: Unified list of customers from both companies.
dim_products: Standardized product catalog with hierarchical categories.
dim_gross_price: Monthly and yearly pricing snapshots.
dim_date: Custom-generated date dimension for time-series analysis.



🚀 Key Features & LogicIncremental Loading: 
Implemented logic to process daily order files from a landing folder and archive them to a processed folder using dbutils.
Schema Enforcement: Leveraged Delta Lake to ensure incoming data types match the target table, preventing data corruption.
Advanced SQL Logic: Created a denormalized "Gold View" to simplify dashboarding, calculating revenue using:
<img width="447" height="57" alt="image" src="https://github.com/user-attachments/assets/10d5d128-6545-4aea-8c64-8e139a73d53c" />
Automated Workflows: Set up a 4-stage job pipeline to ensure data flows sequentially from dimensions to facts.



📈 Dashboard Insights
The final BI dashboard provides a 360-degree view of the merged entity:
Monthly Revenue Trends: Identifying seasonal spikes and acquisition growth.
Top Products/Customers: Ranking performance by both quantity and revenue.
Revenue Share by Channel: Analyzing the impact of direct sales vs. retailers.



👨‍💻 Developed by
Ishaan

