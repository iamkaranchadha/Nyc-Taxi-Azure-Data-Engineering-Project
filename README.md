# Nyc-Taxi-Azure-Data-Engineering-Project

Building a Complete Data Engineering Pipeline with Azure ✨ In this Project, I created a full-fledged end-to-end (E2E) data engineering solution using Azure’s robust ecosystem. The project involves processing, transforming, and delivering data for Business Intelligence (BI) purposes by utilizing key Azure services such as Azure Data Factory, Azure Databricks, delta lake capabilities, and Power BI. The data is sourced from the NYC TAXI govt website ( https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page ) , which is retrieved directly from website. Here's an overview of the solution architecture:

![1746018988484](https://github.com/user-attachments/assets/e5bc019f-5783-438a-8d0c-c67c6fc7f733)


### 📌 Project Objective

The objective of this project is to build an end-to-end **Azure-based data engineering pipeline** that is **scalable**, **efficient**, and **optimized for analytics** using a medallion architecture. The pipeline is designed to:

* **Ingest structured data** from external sources using **Azure Data Factory** for orchestration.
* **Store raw data** in **Azure Data Lake Gen2** in **Parquet format**, providing a cost-effective, scalable, and schema-flexible data lake foundation.
* **Clean, enrich, and transform the data** using **PySpark in Azure Databricks**, following a multi-layered (Bronze → Silver → Gold) data modeling strategy.
* **Store curated data** in the **Delta Lake format** to enable efficient querying and ensure data quality with ACID transaction support.
* **Serve the final transformed data** to **Power BI** for **interactive and insightful reporting** that enables better business decision-making.


### 🧱 Step 1: Setting Up the Azure Environment ⚙️

Provision the core Azure services to support the data pipeline:

* **Azure Data Factory (ADF):** Orchestrates data ingestion from external sources.
* **Azure Data Lake Storage Gen2:** Acts as the data lake with Bronze (raw), Silver (transformed), and Gold (curated) layers.
* **Azure Databricks:** Transforms data using PySpark and writes to **Delta Tables** in the Gold layer.
* **Delta Lake + Delta Tables:** Enables ACID transactions, time travel, and optimized analytics.
* **Power BI:** Connects to Delta Tables for interactive dashboards and business insights.

Each resource was configured with appropriate Identity and Access Management (IAM) roles to ensure secure and seamless connectivity across the environment.

![image](https://github.com/user-attachments/assets/d46bf62c-2206-47d0-bded-b370091dfe66)


### Step 2: Building the Data Pipeline with Azure Data Factory (ADF) 🚀

Azure Data Factory acts as the central orchestrator for the entire data pipeline, enabling dynamic and scalable data ingestion.

* **ForEach Activity for Iteration**: The pipeline uses a **ForEach** activity to loop through a collection of values making the process dynamic and able to handle multiple inputs.

* **Conditional Execution with If Activity**: Inside the **ForEach** loop, an **If Condition** activity is used to apply logic checks—ensuring that only relevant items are processed based on defined conditions.

* **Copy Activity for Data Ingestion**: If the condition is met, a **Copy Activity** fetches data from the NYC Taxi dataset API using an HTTP connector and writes it into the **bronze layer** of Azure Data Lake Storage.

* **Parameterized Pipeline**: Parameters are integrated throughout the pipeline to provide flexibility, allowing dynamic handling of input values and making the pipeline easily adaptable to changes in data source or structure.

![image](https://github.com/user-attachments/assets/897347b0-b007-4c0a-85a1-f38158eee928)

The raw data is now securely stored and ready for transformation.

![image](https://github.com/user-attachments/assets/af817773-de00-4b1b-90c2-c30817292c46)

Step 3: Data Transformation with Azure Databricks 🔄 Using Azure Databricks, the raw data from the bronze container was transformed into a structured format.

Key Steps: Cluster Setup: A Databricks cluster was created to process the data efficiently. Data Lake Integration: Databricks connected to Azure Storage to access the raw data.

![image](https://github.com/user-attachments/assets/2216207f-399e-4de5-8df6-4ad0acde421d)

Transformations: Normalized date formats for consistency.

Cleaned and filtered invalid or incomplete records.

Grouped and concatenated data to make it more usable for analysis.

Saved the transformed data in the silver container in Parquet format for optimal storage and query performance.

![image](https://github.com/user-attachments/assets/7bcf705b-24b4-4a98-8111-b18aa9d35a4c)

![image](https://github.com/user-attachments/assets/90a08d0d-e6aa-4514-9ad0-66ecdc836f28)


### Step 4: Writing to Gold Layer in Delta Format

In this step, I moved the final, refined data from the silver layer to the **gold layer**, storing it in **Delta format** to ensure reliability and performance. I then created a **Delta Table** on top of this data, which serves as a structured and queryable layer. This Delta Table was used as a direct source for **Power BI reports**, enabling fast, real-time analytics and supporting decision-making through interactive dashboards.

![image](https://github.com/user-attachments/assets/c0f27eee-d34f-4f39-a0c3-3d0eac9759ce)


### Step 5: Connecting Power BI to Delta Table Using Cluster Configuration

To enable reporting, I connected **Power BI** to the **Delta Table** in Databricks using **JDBC/ODBC**. I configured the connection using the **Databricks cluster details**, including:

* **Hostname**
* **Port**
* **HTTP Path**
* **Access Token**

This setup ensures secure and direct connectivity, allowing Power BI to query the data in real-time or through scheduled refreshes for dashboarding and analytics.



![Screenshot 2025-05-22 221934](https://github.com/user-attachments/assets/c3efe0e1-1fb3-4be0-83a8-74ccc4396119)



![Screenshot 2025-05-22 222007](https://github.com/user-attachments/assets/e248b426-b6fb-4130-b7a9-939102dbf887)


## 🔧 Project Breakdown – Azure Data Engineering Pipeline

1. **Architecture Design**: Defined a layered architecture (Bronze, Silver, Gold) using Azure Data Lake, ADF, Databricks, and Power BI.

2. **Data Ingestion (ADF)**: Used HTTP connector in a dynamic pipeline with ForEach, If Condition, and Copy activities to load raw data into the **Bronze layer**.

3. **Data Processing (Databricks)**: Transformed and cleaned data from the Bronze layer and stored refined data in the **Silver layer**.

4. **Gold Layer & Delta Table**: Wrote final data to the **Gold layer** in Delta format and created a Delta Table for reporting.

5. **Power BI Connection**: Connected Power BI to the Delta Table using JDBC with cluster hostname, HTTP path, and access token for real-time dashboards.





## 🎯 Key Learnings

1. **ADF Orchestration**: Gained hands-on experience in building dynamic, parameterized pipelines using ForEach, If Condition, and Copy activities.

2. **Layered Architecture**: Understood the importance of organizing data into **Bronze, Silver, and Gold layers** for better data management and scalability.

3. **Delta Lake**: Learned to use **Delta format** for reliable and high-performance data storage and querying.

4. **Databricks Processing**: Improved skills in data transformation and optimization using **Databricks notebooks**.

5. **Power BI Integration**: Set up secure, real-time connectivity between Databricks and **Power BI** using cluster configs and access tokens.

6. **End-to-End Workflow**: Built a complete pipeline from ingestion to visualization, demonstrating the full data lifecycle in Azure.












