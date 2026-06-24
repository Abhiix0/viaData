# ViaData

### Multi-Database Analytics Platform

| Field            | Value                                                            |
| ---------------- | ---------------------------------------------------------------- |
| **Project Name** | ViaData                                                          |
| **Version**      | v1.0                                                             |
| **Status**       | Planning                                                         |
| **Duration**     | 8 Weeks                                                          |
| **Dataset**      | Olist Brazilian E-Commerce Dataset                               |
| **Category**     | Data Engineering / Analytics Engineering / Data Warehousing / BI |

---

# 1. Problem Statement

Most data engineering learners study databases in isolation.

They learn MySQL schemas, PostgreSQL queries, Snowflake warehouses, or BigQuery analytics independently, but rarely understand how these systems interact inside a real enterprise architecture.

**ViaData** solves this problem by simulating a complete enterprise analytics platform where each database serves a distinct business purpose, closely resembling modern production data ecosystems.

---

# 2. Project Vision

Build an end-to-end analytics platform that moves data through four specialized database systems, each optimized for a specific stage of the analytics lifecycle.

```text
MySQL
   ↓
PostgreSQL
   ↓
Snowflake
   ↓
BigQuery
   ↓
Power BI
```

### Platform Responsibilities

| Layer      | Responsibility                        |
| ---------- | ------------------------------------- |
| MySQL      | Operational Source of Truth (OLTP)    |
| PostgreSQL | Business Transformation Layer         |
| Snowflake  | Enterprise Data Warehouse             |
| BigQuery   | Advanced Analytics Layer              |
| Power BI   | Business Intelligence & Visualization |

The system should behave as a connected data platform rather than a collection of independent database exercises.

---

# 3. Target Users

| User Type         | Context                                                  |
| ----------------- | -------------------------------------------------------- |
| Primary Developer | Abhi (B.Tech Data Science, Year 2)                       |
| Audience          | Recruiters, Internship Interviewers, Portfolio Reviewers |
| Goal              | Demonstrate end-to-end Data Engineering capability       |

---

# 4. Dataset

**Source:** Olist Brazilian E-Commerce Dataset (Kaggle)

## Dataset Tables

| Table                        | Approximate Rows |
| ---------------------------- | ---------------- |
| customers                    | ~100,000         |
| orders                       | ~100,000         |
| order_items                  | ~112,000         |
| payments                     | ~103,000         |
| reviews                      | ~99,000          |
| products                     | ~33,000          |
| sellers                      | ~3,000           |
| geolocation                  | ~1,000,000       |
| product_category_translation | Reference Table  |

---

# 5. Functional Requirements

---

## Layer 1: MySQL (Operational Database)

### Objectives

* Load all source tables into a normalized relational schema
* Define Primary Key and Foreign Key constraints
* Implement indexing strategy
* Support transactional and operational workloads
* Measure query performance

### Deliverables

* Entity Relationship Diagram (ERD)
* Schema Creation Scripts
* Index Documentation
* Query Benchmark Report

### Success Criteria

* All source tables loaded successfully
* Referential integrity enforced
* Queries optimized using indexes

---

## Layer 2: PostgreSQL (Transformation Layer)

### Objectives

Extract data from MySQL and create reusable business models.

### Metric Tables

```sql
customer_metrics
seller_metrics
product_metrics
delivery_metrics
revenue_metrics
```

### Advanced SQL Requirements

Implement at least:

* 15+ SQL transformations
* Common Table Expressions (CTEs)
* Window Functions

  * LEAD()
  * LAG()
  * RANK()
  * DENSE_RANK()
* Aggregation pipelines

### Materialized Views

Create at least five reusable analytical views.

### Deliverables

* Transformation SQL Library
* Metrics Catalog
* Materialized Views

### Success Criteria

* All business metrics validated
* Materialized views refresh successfully

---

## Layer 3: Snowflake (Enterprise Warehouse)

### Objectives

Design and implement a dimensional warehouse.

### Fact Tables

```sql
fact_orders
fact_order_items
fact_payments
fact_reviews
```

### Dimension Tables

```sql
dim_customer
dim_product
dim_seller
dim_date
dim_location
dim_payment
```

### Deliverables

* Star Schema Design
* Warehouse DDL Scripts
* Data Load Scripts
* Warehouse Documentation

### Success Criteria

* Fact tables populated correctly
* Dimensions fully connected
* Star schema validated

---

## Layer 4: BigQuery (Analytics Layer)

### Objectives

Build enterprise analytics models.

### Required Analytical Models

* Customer Lifetime Value (CLV)
* Cohort Analysis
* Retention Analysis
* Revenue Trends
* Product Trends
* Seller Rankings
* Geographic Performance
* Delivery Performance

### Optimization Requirements

* Partitioning
* Clustering
* Query Cost Optimization

### Deliverables

* Analytics SQL Library
* Analytical Datasets
* KPI Documentation

### Success Criteria

* All analytical models validated
* Optimized query performance

---

## Layer 5: Power BI (Visualization Layer)

### Objectives

Build production-quality dashboards.

### Dashboards

| Dashboard               | Focus Area               |
| ----------------------- | ------------------------ |
| Executive Overview      | Revenue, Orders, Growth  |
| Customer Intelligence   | CLV, Retention, Segments |
| Seller Intelligence     | Revenue, Ratings, Growth |
| Product Intelligence    | Products, Categories     |
| Geographic Intelligence | Revenue by Region        |

### Success Criteria

* Business questions answerable visually
* KPIs clearly represented

---

# 6. ETL Requirements

## Pipeline Flow

```text
Extract
   ↓
Validate
   ↓
Transform
   ↓
Load
   ↓
Monitor
```

---

## Incremental Loading Strategy

| Property        | Detail                   |
| --------------- | ------------------------ |
| First Run       | Full Historical Load     |
| Subsequent Runs | Incremental Loads        |
| Tracking Column | order_purchase_timestamp |
| Metadata Table  | etl_watermarks           |

### Watermark Table Structure

```sql
pipeline_name
last_processed_timestamp
```

### Goal

Prevent unnecessary full reloads and simulate real-world ingestion pipelines.

---

# 7. Data Quality Requirements

## Validation Rules

| Entity    | Validation Rule                      |
| --------- | ------------------------------------ |
| Orders    | Unique order_id and valid timestamps |
| Customers | Non-null customer IDs                |
| Payments  | payment_value > 0                    |
| Reviews   | review_score BETWEEN 1 AND 5         |

---

## Quality Tables

### data_quality_log

Stores validation results.

### failed_records

Stores rejected records for investigation.

### Enforcement Policy

Critical validation failures immediately stop pipeline execution.

---

# 8. Monitoring Requirements

## etl_runs

| Column           | Description                  |
| ---------------- | ---------------------------- |
| run_id           | Unique pipeline execution ID |
| start_time       | Pipeline start timestamp     |
| end_time         | Pipeline end timestamp       |
| status           | Success / Failure            |
| rows_processed   | Number of processed rows     |
| duration_seconds | Total execution duration     |

---

## pipeline_logs

| Column    | Description      |
| --------- | ---------------- |
| stage     | Pipeline stage   |
| status    | Execution status |
| message   | Log message      |
| timestamp | Event timestamp  |

---

# 9. KPI Catalog

## Revenue KPIs

* Total Revenue
* Average Order Value
* Monthly Revenue
* Revenue Growth Rate
* Revenue by Category
* Revenue by Seller

---

## Customer KPIs

* Customer Lifetime Value
* Repeat Purchase Rate
* Retention Rate
* Average Customer Spend
* Orders per Customer

---

## Seller KPIs

* Revenue per Seller
* Orders per Seller
* Average Seller Rating
* Seller Growth Rate

---

## Delivery KPIs

* Average Delivery Time
* Late Delivery Percentage
* Average Freight Cost

---

## Product KPIs

* Units Sold
* Revenue per Product
* Revenue per Category
* Category Growth Rate

---

# 10. Non-Functional Requirements

| Requirement         | Target                                        |
| ------------------- | --------------------------------------------- |
| Reproducibility     | Complete rebuild from raw CSV files           |
| Portability         | Config-driven connections                     |
| Testability         | Unit and Integration Tests                    |
| Documentation       | Complete architecture and model documentation |
| Interview Readiness | Architecture explainable under pressure       |

---

# 11. Technology Stack

| Layer                | Technology                 |
| -------------------- | -------------------------- |
| Language             | Python 3.12+               |
| ORM / Database       | SQLAlchemy                 |
| MySQL Connector      | PyMySQL                    |
| PostgreSQL Connector | psycopg2-binary            |
| Snowflake Connector  | snowflake-connector-python |
| BigQuery Connector   | google-cloud-bigquery      |
| Data Processing      | pandas, pyarrow            |
| Configuration        | python-dotenv              |
| Visualization        | Power BI                   |
| Package Management   | uv                         |

---

# 12. Development Roadmap

| Phase | Name                            | Key Outputs                                           | Exit Condition              |
| ----- | ------------------------------- | ----------------------------------------------------- | --------------------------- |
| 1     | Data Understanding & Modeling   | Profiling, Data Dictionary, ERD, Architecture Diagram | Dataset fully understood    |
| 2     | MySQL Operational Layer         | Schema, Constraints, Indexes, Benchmarks              | Source system operational   |
| 3     | PostgreSQL Transformation Layer | Metrics, Views, Advanced SQL                          | Metrics validated           |
| 4     | ETL Engine                      | Watermarks, Logging, Incremental Loads                | End-to-End Pipeline Working |
| 5     | Snowflake Warehouse             | Star Schema, Facts, Dimensions                        | Warehouse populated         |
| 6     | BigQuery Analytics              | CLV, Cohorts, Retention Models                        | Analytics validated         |
| 7     | Power BI Dashboards             | 5 Production Dashboards                               | Business insights available |
| 8     | Production Hardening            | Testing, Optimization, Documentation                  | Interview Ready             |

---

# 13. Success Criteria

The project is considered complete when:

* [ ] MySQL operational layer is fully functional
* [ ] PostgreSQL transformation layer is implemented
* [ ] Snowflake warehouse is populated
* [ ] BigQuery analytical models are validated
* [ ] Incremental ETL loading works correctly
* [ ] Data quality checks are enforced and blocking
* [ ] Monitoring and logging are operational
* [ ] Five Power BI dashboards answer defined business questions
* [ ] Full architecture can be confidently explained during technical interviews
* [ ] Project is portfolio-ready and production-style

---

# 14. Final Architecture

```text
                   Olist Dataset (CSV)
                            │
                            ▼
                   MySQL (Operational)
                            │
                            ▼
               PostgreSQL (Transformations)
                            │
                            ▼
                 Snowflake (Warehouse)
                            │
                            ▼
                 BigQuery (Analytics)
                            │
                            ▼
                   Power BI Dashboards
```

### Core Principle

> Each database exists for a specific reason.
> The goal of ViaData is not to store data in multiple systems, but to demonstrate how modern enterprise data platforms move, transform, warehouse, analyze, and visualize data across specialized layers.
