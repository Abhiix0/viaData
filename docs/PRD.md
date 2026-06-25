# ViaData

## Modern Analytics Engineering Laboratory

**Version:** v1.0
**Status:** Planning
**Duration:** 8-10 Weeks
**Dataset:** Olist Brazilian E-Commerce Dataset

---

# 1. Executive Summary

ViaData is a hands-on analytics engineering laboratory designed to develop practical experience across multiple database technologies and modern data platform concepts.

Rather than treating databases as interchangeable storage systems, ViaData assigns a dedicated responsibility to each technology:

| Technology      | Learning Focus                       |
| --------------- | ------------------------------------ |
| MySQL           | Database Engineering & OLTP          |
| PostgreSQL      | Analytics Engineering & Advanced SQL |
| Snowflake       | Data Warehousing                     |
| BigQuery        | Large-Scale Analytics                |
| Power BI        | Business Intelligence                |
| Python + Polars | Data Engineering & ETL               |

The project uses a single business domain (e-commerce) while exploring how different platforms solve different categories of problems.

The primary objective is learning architecture patterns, SQL mastery, warehouse modeling, pipeline development, and analytical thinking.

---

# 2. Project Vision

Modern data professionals rarely work with a single technology.

A strong analytics engineer understands:

* Operational databases
* Data transformation workflows
* Data warehouse design
* Analytical modeling
* Business intelligence systems
* Data quality processes
* Pipeline automation

ViaData is designed as a structured learning environment where each layer teaches a specific discipline while contributing to a complete analytics platform.

---

# 3. Learning Objectives

## MySQL

Learn:

* Relational schema design
* Normalization
* Foreign key constraints
* Indexing strategies
* Query optimization
* Transactions
* EXPLAIN plans
* OLTP concepts

---

## PostgreSQL

Learn:

* Advanced SQL
* Common Table Expressions
* Window Functions
* Materialized Views
* Business metric modeling
* Analytical SQL patterns

Required concepts:

* CTE
* Window Functions
* LEAD
* LAG
* RANK
* DENSE_RANK
* PARTITION BY
* Materialized Views

---

## Snowflake

Learn:

* Dimensional modeling
* Star schema design
* Fact tables
* Dimension tables
* Warehouse loading
* Clustering concepts
* Historical storage patterns

---

## BigQuery

Learn:

* Analytical datasets
* Cohort analysis
* Retention analysis
* Customer lifetime value
* Query optimization
* Partitioning
* Clustering
* Cost-aware analytics

---

## Data Engineering

Learn:

* ETL pipelines
* Incremental loading
* Data validation
* Metadata tracking
* Logging
* Pipeline monitoring
* Error handling

---

## Analytics Engineering

Learn:

* Metric layer design
* Reusable transformations
* Business logic abstraction
* Data quality testing
* Documentation practices

---

# 4. Dataset Analysis

## Source Dataset

Olist Brazilian E-Commerce Dataset

## Core Tables

* customers
* orders
* order_items
* payments
* reviews
* products
* sellers
* geolocation
* product_category_translation

Dataset Size:

* ~100k Orders
* ~100k Customers
* ~112k Order Items
* ~103k Payments
* ~99k Reviews
* ~33k Products
* ~3k Sellers
* ~1M Geolocation Records

---

# 5. Architecture

## High-Level Architecture

```text
Olist Dataset
       │
       ▼

MySQL
(Database Engineering Lab)

       ▼

Python + Polars ETL

       ▼

PostgreSQL
(SQL & Transformation Lab)

       ▼

Snowflake
(Data Warehouse Lab)

       ▼

BigQuery
(Analytics Lab)

       ▼

Power BI
(Business Intelligence)
```

---

# 6. Layer Responsibilities

## Layer 1: MySQL

### Purpose

Database Engineering Laboratory

### Responsibilities

* Store normalized source data
* Implement constraints
* Implement indexing
* Analyze query performance
* Simulate operational workloads

### Deliverables

* ER Diagram
* Schema Scripts
* Index Strategy
* Query Benchmark Report

### Success Criteria

* Fully normalized schema
* Proper FK relationships
* Optimized indexes
* Performance benchmarks documented

---

## Layer 2: Python + Polars ETL

### Purpose

Data Engineering Laboratory

### Responsibilities

* Data extraction
* Validation
* Transformation
* Loading
* Metadata tracking

### Features

* Full Loads
* Incremental Loads
* Watermark Tracking
* Error Handling
* Retry Logic

### Deliverables

* ETL Framework
* Validation Engine
* Metadata Tracking Tables

---

## Layer 3: PostgreSQL

### Purpose

Analytics Engineering Laboratory

### Responsibilities

* Build business metrics
* Create analytical datasets
* Implement advanced SQL patterns

### Output Models

* customer_metrics
* seller_metrics
* product_metrics
* delivery_metrics
* revenue_metrics

### Required Deliverables

* 15+ SQL transformations
* 5+ Materialized Views
* Metrics Catalog
* SQL Library

---

## Layer 4: Snowflake

### Purpose

Data Warehouse Laboratory

### Responsibilities

* Historical storage
* Reporting optimization
* Dimensional modeling

### Fact Tables

* fact_orders
* fact_order_items
* fact_payments
* fact_reviews

### Dimension Tables

* dim_customer
* dim_product
* dim_seller
* dim_date
* dim_location

### Deliverables

* Star Schema
* Warehouse Documentation
* Load Scripts

---

## Layer 5: BigQuery

### Purpose

Advanced Analytics Laboratory

### Analytical Models

* Customer Lifetime Value
* Cohort Analysis
* Retention Analysis
* Revenue Trends
* Product Trends
* Seller Rankings
* Geographic Performance
* Delivery Analytics

### Deliverables

* Analytics SQL Library
* Analytical Datasets
* KPI Documentation

---

# 7. Data Quality Framework

## Validation Rules

### Orders

* Unique order_id
* Valid timestamps

### Customers

* Non-null customer_id

### Payments

* payment_value > 0

### Reviews

* review_score between 1 and 5

## Tables

### data_quality_log

Tracks validation failures.

### failed_records

Stores rejected records.

### Success Criteria

Critical validation failures stop pipeline execution.

---

# 8. Incremental Loading Strategy

## Initial Run

Full Historical Load

## Incremental Runs

Watermark Based Loading

### Metadata Table

etl_watermarks

Columns:

* pipeline_name
* last_processed_timestamp

### Late Arriving Data Strategy

Overlap Window:

```text
Reload Previous 3 Days
Deduplicate Records
```

Purpose:

* Capture delayed records
* Simulate real-world ingestion patterns

---

# 9. Monitoring & Observability

## Pipeline Metrics

* Rows Processed
* Rows Inserted
* Rows Updated
* Rows Failed
* Runtime Duration
* Pipeline Status
* Data Freshness

## Tables

### etl_runs

Stores execution history.

### pipeline_logs

Stores detailed execution logs.

### pipeline_metrics

Stores operational metrics.

---

# 10. KPI Catalog

## Revenue KPIs

* Total Revenue
* Average Order Value
* Monthly Revenue
* Revenue Growth Rate

## Customer KPIs

* Customer Lifetime Value
* Retention Rate
* Repeat Purchase Rate
* Average Customer Spend

## Seller KPIs

* Revenue Per Seller
* Seller Growth Rate
* Seller Rating

## Product KPIs

* Units Sold
* Revenue Per Product
* Category Growth Rate

## Delivery KPIs

* Delivery Time
* Late Delivery %
* Freight Cost

---

# 11. Dashboards

## Executive Dashboard

Business Health Overview

## Customer Dashboard

CLV, Retention, Segmentation

## Seller Dashboard

Revenue, Ratings, Growth

## Product Dashboard

Performance, Trends, Categories

## Geographic Dashboard

Revenue & Delivery Analysis

---

# 12. Repository Structure

```text
via-data/

data/

mysql/
postgres/
snowflake/
bigquery/

pipelines/
  extract/
  transform/
  load/

monitoring/
tests/
dashboards/
docs/

README.md
```

---

# 13. Roadmap

## Phase 1

Data Profiling & Modeling

## Phase 2

MySQL Database Engineering

## Phase 3

Python ETL Framework

## Phase 4

PostgreSQL Analytics Engineering

## Phase 5

Snowflake Data Warehouse

## Phase 6

BigQuery Analytics

## Phase 7

Power BI Dashboards

## Phase 8

Testing & Production Hardening

---

# 14. Final Success Metrics

Project is complete when:

* All database layers operational
* ETL framework functioning
* Incremental loading implemented
* Data quality checks enforced
* Star schema implemented
* Analytical models validated
* Dashboards answer business questions
* Architecture fully documented
* All technologies can be explained confidently during interviews

---

# Final Outcome

ViaData becomes a complete Analytics Engineering Laboratory demonstrating practical experience in:

* Database Engineering
* Data Engineering
* Analytics Engineering
* Data Warehousing
* Business Intelligence

while providing hands-on exposure to MySQL, PostgreSQL, Snowflake, BigQuery, Power BI, and modern ETL practices.
