# 🏗️ E-Commerce Data Engineering Pipeline (Medallion Architecture) 

## 📌 Overview

This project implements an **end-to-end data engineering pipeline** using the **Medallion Architecture (Bronze → Silver → Gold)** on Databricks.

It includes:

* Data ingestion
* Data transformation
* Data modeling
* Performance optimization
* CI/CD using GitHub Actions

---

## 🧱 Architecture

```
Bronze Layer  → Raw Data Ingestion  
Silver Layer  → Clean + Deduplicated + Enriched Data  
Gold Layer    → Business Aggregations (Fact & Dimensions)
```

---

## ⚙️ Tech Stack

* **Databricks (Spark + Delta Lake)**
* **Python / PySpark**
* **Unity Catalog**
* **GitHub**
* **GitHub Actions (CI/CD)**

---

## 🥉 Bronze Layer

### Features:

* Ingest raw data from source files
* Store in Delta format
* Append-only strategy

### Output Tables:

* `bronze_customers`
* `bronze_products`
* `bronze_orders`
* `bronze_order_items`

---

## 🥈 Silver Layer

### Features:

* Incremental processing using timestamps
* Deduplication using window functions
* Merge (UPSERT) using Delta Lake
* Data enrichment (joins)

### Output Tables:

* `silver_customers`
* `silver_products`
* `silver_orders`
* `silver_order_items`
* `silver_orders_enriched`

---

## 🥇 Gold Layer

### Data Modeling:

* `fact_sales`
* `dim_customers`
* `dim_products`

### Aggregations:

* Revenue by state
* Top products
* Sales trends (daily/monthly)

---

## ⚡ Spark Optimizations

* Broadcast joins for small tables
* Repartition for parallelism
* Partitioning by `state`
* Caching for repeated queries
* Handling skewed data

---

## 🧊 Delta Lake Features

* OPTIMIZE with Z-ORDER
* VACUUM (data cleanup)
* Time Travel
* Schema enforcement
* Partition pruning

---

## 🔄 CI/CD Pipeline

### Implemented using:

* Databricks Asset Bundles
* GitHub Actions

### Workflow:

```
Code Push → GitHub Actions → Databricks Deploy
```

### Features:

* Automated deployment
* Environment support (dev / uat / prod)
* Secure secrets management

---

## 🌍 Environment Setup

| Environment | Catalog |
| ----------- | ------- |
| Dev         | dev     |
| UAT         | uat     |
| Prod        | prod    |

---

## 🚀 How to Run

### 1. Validate Bundle

```
databricks bundle validate
```

### 2. Deploy

```
databricks bundle deploy -t dev
```

### 3. Run Pipeline

```
databricks bundle run ecom_pipeline -t dev
```

---

## 📊 Pipeline Flow

```
Bronze → Silver → Gold
```

Each layer improves:

* Data quality
* Performance
* Business usability

---

## 🧠 Key Learnings

* End-to-end pipeline design
* Incremental data processing
* Delta Lake optimization
* CI/CD for data engineering
* Real-world production practices

---

## 👨‍💻 Author

**Vijay Gupta**

---

## ⭐ Conclusion

This project demonstrates a **production-ready data engineering pipeline** with:

* Scalable architecture
* Optimized Spark jobs
* Automated deployment
