#### Log Analytics Dashboard

##### Project Overview

* End-to-end data engineering pipeline
* Data ingested from API → processed → visualized in Power BI
* Simulates real-world log data processing



##### Data Source

* API: JSONPlaceholder
* Posts (100 records) → log data
* Comments (500 records) → user interactions



##### Data Pipeline

* Orchestrated using Azure Data Factory
* Pipeline flow:
* Copy posts \& comments (API → Data Lake)
* Run Databricks notebooks (Bronze → Silver → Gold)



##### Medallion Architecture

###### Bronze Layer

* Raw JSON stored as-is
* Added ingestion timestamp
* Append mode (keeps history)
* 

###### Silver Layer

* Data cleaning \& transformation
* Removed duplicates \& nulls
* Text standardization (trim, lowercase)
* New columns:
* body\_length
* log\_level (ERROR/INFO)
* is\_error flag
* email validation
* Incremental load using MERGE



###### Gold Layer

Aggregated business-level data

Examples:

Posts per user

Comments per post

Errors per user

User activity

Optimized for reporting



##### Dashboard (Power BI)

* Tool: Microsoft Power BI
* KPIs:

&#x20;      Total Posts (100)

&#x20;      Total Comments (500)

&#x20;      Avg Comments/Post (5)

&#x20;      Active Users (10)

* Visuals:

&#x20;      Posts per user (bar chart)

&#x20;      Post details table

&#x20;      Error details

&#x20;      Word cloud

&#x20;      Body length analysis

&#x20;      Top 10 posts

&#x20;      User contribution (donut chart)

* Filters: User ID, Email, Post ID



##### Tools Used

* Azure Data Factory
* Azure Data Lake Storage Gen2
* Azure Databricks
* Apache Spark, Delta Lake
* Microsoft Power BI
* Python, PySpark

&#x20;       

