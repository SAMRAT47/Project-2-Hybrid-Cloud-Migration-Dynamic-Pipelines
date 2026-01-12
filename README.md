# Azure Hybrid Cloud Data Engineering Project: Dynamic ETL & Migration

![Project Thumbnail](https://github.com/SAMRAT47/Project-2-Hybrid-Cloud-Migration-Dynamic-Pipelines/blob/main/Images/project2%20thumbnail.png)
## 📋 Project Overview
This project demonstrates an end-to-end **Hybrid Cloud Data Engineering solution** on Microsoft Azure. It simulates a real-world scenario where data is migrated from diverse sources—including on-premise file servers, HTTP APIs, and SQL Databases—into a centralized Data Lakehouse.

The solution implements the **Medallion Architecture** (Bronze, Silver, Gold) using **Azure Data Factory (ADF)** for orchestration and **Mapping Data Flows** for low-code Spark-based transformations. It features advanced capabilities such as **incremental loading (watermarking)**, **dynamic parameterization**, and **automated alerting** via Logic Apps.

## 🏗️ Solution Architecture
The architecture follows a modern Lakehouse approach, moving data through three stages of quality:

![Solution Architecture Diagram](https://github.com/SAMRAT47/Project-2-Hybrid-Cloud-Migration-Dynamic-Pipelines/blob/main/Images/project2%20Architecture.png)
1.  **Bronze Layer (Raw):** Ingests data "as-is" from source systems.
2.  **Silver Layer (Cleaned):** Data cleaning, standardization, and schema validation.
3.  **Gold Layer (Curated):** Aggregated data ready for business reporting and analytics.

---



## 🛠️ Tech Stack & Tools
* **Orchestration:** Azure Data Factory (ADF) V2
* **Storage:** Azure Data Lake Storage Gen2 (ADLS)
* **Compute:** Azure Integration Runtimes (Auto-Resolve & Self-Hosted)
* **Database:** Azure SQL Database
* **Transformation:** ADF Mapping Data Flows (Spark Cluster)
* **Monitoring:** Azure Logic Apps & Azure Monitor
* **DevOps:** Git Integration (Azure DevOps/GitHub)

  ** 🛠️ Services inside Azure Resource Groups:**

  ![ResourceGroup Image](https://github.com/SAMRAT47/Project-2-Hybrid-Cloud-Migration-Dynamic-Pipelines/blob/main/Images/project2%20resource%20group.PNG)

---

## 🚀 Key Modules

### 1. Data Ingestion (Bronze Layer)
This module handles the extraction of data from three distinct sources, showcasing versatility in handling hybrid environments.

![OnPrem Ingestion Pipelines](https://github.com/SAMRAT47/Project-2-Hybrid-Cloud-Migration-Dynamic-Pipelines/blob/main/Images/OnPrem%20Ingesion.PNG)

* **On-Premise Files:** Uses a **Self-Hosted Integration Runtime** to securely connect to a local machine/private network and migrate file-based data to the cloud.
  
![API Ingestion Pipelines](https://github.com/SAMRAT47/Project-2-Hybrid-Cloud-Migration-Dynamic-Pipelines/blob/main/Images/API%20Ingestion%20pipeline.PNG)

* **HTTP/REST API:** Dynamically fetches raw JSON data from web endpoints (simulated using GitHub raw content).

![SQL Ingestion Pipelines](https://github.com/SAMRAT47/Project-2-Hybrid-Cloud-Migration-Dynamic-Pipelines/blob/main/Images/SQL%20to%20Datalake%20ingestion.PNG)

* **Azure SQL Database (Incremental Load):** Implements a **Watermarking Pattern**. It tracks the `LastModifiedDate` to fetch only new or updated records since the last run, optimizing performance.


* **HTTP/REST API:** Dynamically fetches raw JSON data from web endpoints (simulated using GitHub raw content).
* **On-Premise Files:** Uses a **Self-Hosted Integration Runtime** to securely connect to a local machine/private network and migrate file-based data to the cloud.
* **Azure SQL Database (Incremental Load):** Implements a **Watermarking Pattern**. It tracks the `LastModifiedDate` to fetch only new or updated records since the last run, optimizing performance.

### 2. Data Transformation (Silver Layer)
Raw data is processed using **ADF Mapping Data Flows**, providing a visual interface for complex Spark logic without writing code.

![Data Transformation Flow](https://github.com/SAMRAT47/Project-2-Hybrid-Cloud-Migration-Dynamic-Pipelines/blob/main/Images/Data%20Transformation.PNG)
* **Data Cleaning:** Handling NULL values, casting data types (e.g., String to Integer), and removing duplicates.
* **Standardization:** Renaming columns to camelCase and formatting dates for consistency.
* **Schema Drift:** Handling dynamic schema changes from sources automatically.

### 3. Business Logic & Serving (Gold Layer)
The final layer prepares data for consumption by analytical tools (like Power BI).

![Data Serving Logic](https://github.com/SAMRAT47/Project-2-Hybrid-Cloud-Migration-Dynamic-Pipelines/blob/main/Images/Data%20Serving.PNG)
* **Joins:** Combining Fact and Dimension tables (e.g., Joining `Sales` with `Customer` data).
* **Aggregations & Window Functions:** Calculating metrics like *Total Revenue per Region* and using `Dense_Rank` to identify top-performing products.
* **Upsert Logic:** Using Delta Lake capabilities to update existing records and insert new ones (Merge operation).

### 4. Orchestration & Alerting
The entire workflow is automated and monitored for reliability.

![Logic App Alert](https://github.com/SAMRAT47/Project-2-Hybrid-Cloud-Migration-Dynamic-Pipelines/blob/main/Images/Logic%20App%20Alart.PNG)
* **Master Pipeline:** A parent pipeline executes child pipelines in a specific sequence using `Execute Pipeline` activities.
* **Error Handling:** Try-Catch logic is implemented to capture failures.
* **Automated Alerts:** An **Azure Logic App** is triggered via Webhooks upon pipeline failure, sending a customized email notification with the *Pipeline Name*, *Error Message*, and *Run ID*.

---

## 💡 Key Learnings & Features
* **Dynamic Pipelines:** Utilized parameters and variables to create reusable pipelines (e.g., a single pipeline handles multiple file types by passing the filename as a parameter).
* **Security:** Secured connections using Key Vault (best practice simulation) and Self-Hosted IR for private network access.
* **CI/CD:** Configured Git integration for version control, branching strategies, and collaboration.

## 👤 Author
**Samrat**
* [LinkedIn Profile](https://www.linkedin.com/in/samrat-roychoudhury/)
* [Mail Id](samrat.networkwan@gmail.com)

---
*Note: This project serves as a proof-of-concept for modern cloud data migration strategies.*
