* Data Warehouse Project



Project Overview
This project implements an end-to-end data warehouse solution using SQL Server, designed to transform raw operational data into actionable business intelligence. The architecture follows the classic three-layer data warehouse pattern: Bronze (raw), Silver (cleaned), and Golden (business-ready) layers.
Architecture
The data warehouse follows a medallion architecture with three distinct layers:
1. Bronze Layer (Raw Data Ingestion)

Purpose: Initial landing zone for raw data from source systems
Object Type: Tables
Load Strategy:

Batch processing
Incremental loads
Change Data Capture (CDC)
Full & Incremental loads


Data Model: None (raw schema preservation)
Transformations: None (data stored as-is)

2. Silver Layer (Cleaned & Standardized)

Purpose: Cleansed and validated data ready for business logic
Object Type: Tables
Load Strategy:

Batch processing
Incremental updates
Full load
Truncate & Load


Transformations:

Data cleansing
Standardization
Normalization
Deduplication
Schema enforcement


Data Model: None (still in relational format)

3. Golden Layer (Business-Ready Analytics)

Purpose: Business-optimized data for reporting and analytics
Object Type: Views
Load Strategy: No load (views query Silver layer)
Transformations:

Aggregation
Denormalization
Business logic application


Data Model:

Star Schema
Fact tables
Dimension tables
Aggregate tables



Data Sources
The warehouse ingests data from multiple operational systems:

CRM System: Customer relationship data

Object Type: CSV files
Interface: Files in folders


ERP System: Enterprise resource planning data

Object Type: CSV files
Interface: Files in folders



Data Consumers
The processed data serves multiple analytical purposes:

BI & Reporting: Dashboards and operational reports
SQL Queries: Ad-hoc analysis and data exploration
Machine Learning: Training datasets for predictive models

Technology Stack

Database Platform: Microsoft SQL Server
ETL/ELT: SQL Server Integration Services (SSIS) / T-SQL stored procedures
Data Format: CSV files (source), Relational tables (warehouse)
Version Control: Git

Project Structure

<img width="4164" height="2608" alt="image" src="https://github.com/user-attachments/assets/bf6d3735-32a5-4f09-8aaf-23e9db4674be" />


Data Flow

Extraction: Raw data extracted from CRM and ERP systems as CSV files
Bronze Load: CSV files loaded into Bronze layer tables with minimal transformation
Silver Transformation: Data cleansed, validated, and standardized in Silver layer
Golden Modeling: Business views created on top of Silver layer using star schema
Consumption: End users query Golden layer for analytics, reporting, and ML

Key Features

Incremental Loading: Efficient data updates using CDC and incremental patterns
Data Quality: Built-in validation and cleansing in Silver layer
Scalability: Layered architecture allows independent scaling of each tier
Auditability: Full lineage tracking from source to consumption
Performance: Star schema optimization for analytical queries
Flexibility: Views in Golden layer allow schema changes without data reloading

Getting Started
Prerequisites

SQL Server 2019 or later
SQL Server Management Studio (SSMS)
Access to source system data files

Installation

Clone this repository
Execute Bronze layer scripts in /sql/bronze/
Execute Silver layer scripts in /sql/silver/
Execute Golden layer scripts in /sql/golden/
Run initial data load procedures

Configuration

Update connection strings in ETL scripts
Configure file paths for CSV ingestion
Set up SQL Server Agent jobs for scheduled loads

Contributing
Please read CONTRIBUTING.md for details on our code of conduct and the process for submitting pull requests.
License
This project is licensed under the MIT License - see the LICENSE.md file for details.
Contact
For questions or support, please open an issue in this repository.

Project Status: In Development
Last Updated: October 2025
