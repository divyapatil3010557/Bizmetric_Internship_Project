## Log Analytics 
Project Overview
End-to-end data engineering pipeline
Data ingested from API → processed → visualized in Power BI
Simulates real-world log data processing

## Data Source
API: JSONPlaceholder
Posts (100 records) → log data
Comments (500 records) → user interactions

##  Data Pipeline
<img width="1613" height="206" alt="image" src="https://github.com/user-attachments/assets/009a39f5-fc42-4294-ab67-5ec9e42b32f0" />

Orchestrated using Azure Data Factory
Pipeline flow:
Copy posts & comments (API → Data Lake)
Run Databricks notebooks (Bronze → Silver → Gold)

## Medallion Architecture
Bronze Layer
Raw JSON stored as-is
Added ingestion timestamp
Append mode (keeps history)

Silver Layer
Data cleaning & transformation
Removed duplicates & nulls
Text standardization (trim, lowercase)
New columns:
body_length
log_level (ERROR/INFO)
is_error flag
email validation
Incremental load using MERGE

Gold Layer
Aggregated business-level data
Examples:
Posts per user
Comments per post
Errors per user
User activity
Optimized for reporting

## Dashboard (Power BI)
<img width="383" height="474" alt="image" src="https://github.com/user-attachments/assets/6c3e62cc-b000-4905-b81e-576174945be5" />
Tool: Microsoft Power BI
KPIs:
       Total Posts (100)
       Total Comments (500)
       Avg Comments/Post (5)
       Active Users (10)
Visuals:
       Posts per user (bar chart)
       Post details table
       Error details
       Word cloud
       Body length analysis
       Top 10 posts
       User contribution (donut chart)
Filters: User ID, Email, Post ID

## Tools Used
Azure Data Factory
Azure Data Lake Storage Gen2
Azure Databricks
Apache Spark, Delta Lake
Microsoft Power BI
Python, PySpark
