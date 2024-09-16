# Azure Data Pipeline Project

This repository contains the setup, configuration, and implementation details for an Azure Data Pipeline project. The pipeline is designed to ingest, transform, and load data from SQL Server into Azure Synapse Analytics and Power BI.

## Project Breakdown

### 1. Environmental Setup

1. **Microsoft SQL Server and SSMS**
2. **Azure Portal**
3. **Resource Group**
4. **Azure Data Factory (V2)**
5. **Azure Databricks Service**
6. **Azure Key Vault**
7. **Storage Account (ADLS Gen 2)**
8. **Synapse Analytics Workspace**
9. **Access Control (IAM)**
   - Owner
   - Azure Active Directory Security Group
   - Storage Blob Data Container - User and Managed Identity
   - Storage Blob Data Reader - User and Managed Identity
10. **Key Vault**
    - Username
    - Password
    - Databricks Access Token

### 2. Data Ingestion

1. **Azure Data Factory**
   - Self-Hosted Integration Runtime (for SQL Server)
   - Auto Resolve Integration Runtime (for ADLS Gen 2)
2. **Linked Service**
   - SQL Server
   - ADLS Gen 2
   - Key Vault
3. **Pipeline**
   - Lookup Tables
   - For Each Table - Copy Data Activity
   - Parquet Data Format
   - Data Ingestion into Bronze Container

### 3. Data Transformation

1. **Azure Databricks**
   - Access Token
   - Compute - Cluster Creation
   - Workspace
   - Notebooks
     - Storage Mount - To Mount ADLS Gen 2 Containers
     - Bronze to Silver - PySpark
     - Silver to Gold - PySpark

2. **Azure Data Factory**
   - Linked Service
   - Azure Databricks
   - Pipeline
   - Lookup Tables
   - For Each - Copy Data into Bronze Container
   - Bronze to Silver Databricks Notebook
   - Silver to Gold Databricks Notebook

### 4. Data Loading

1. **Azure Synapse Analytics (Synapse Studio)**
   - Create Serverless SQL Database
   - SQL Scripts - Stored Procedure Script
   - Linked Service
   - Azure SQL Database
   - From Synapse Workspace Properties - Collect Serverless SQL Endpoint
   - Integrate - Pipeline - Views Creation
   - Get Metadata - Binary Format - Connect to Gold Container
   - For Each - Stored Procedure Activity

### 5. Data Reporting

1. **Power BI**
   - Get Data - Azure - Synapse Analytics (SQL DW)
   - Provide Credentials and Sign in to your Microsoft Account
   - Select and Load Data Tables
   - Create Visuals and Develop Relevant Dashboard

## Setup Instructions

1. **Environmental Setup**
   - Follow Azure documentation to set up required services and configurations.
   - Ensure appropriate access control is in place.

2. **Data Ingestion**
   - Configure Azure Data Factory to connect to SQL Server and ADLS Gen 2.
   - Set up pipelines and linked services for data ingestion.

3. **Data Transformation**
   - Set up Azure Databricks workspace and clusters.
   - Create and run PySpark notebooks for data transformation.

4. **Data Loading**
   - Configure Synapse Analytics for data loading and serverless SQL queries.
   - Implement pipelines and stored procedures for data processing.

5. **Data Reporting**
   - Connect Power BI to Synapse Analytics.
   - Build and publish dashboards using the ingested and transformed data.

## Additional Resources

- [Azure Data Factory Documentation](https://docs.microsoft.com/en-us/azure/data-factory/)
- [Azure Databricks Documentation](https://docs.microsoft.com/en-us/azure/databricks/)
- [Azure Synapse Analytics Documentation](https://docs.microsoft.com/en-us/azure/synapse-analytics/)
- [Power BI Documentation](https://docs.microsoft.com/en-us/power-bi/)

##

Thank you!
