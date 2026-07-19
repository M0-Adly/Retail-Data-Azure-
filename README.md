# 🏪 Retail Transactions Medallion Pipeline

**Enterprise-grade Lakehouse ETL & Analytics Platform** built on Azure Synapse Analytics, implementing the **Medallion Architecture** (Bronze → Silver → Gold) to transform raw daily retail transactions into a governed, star-schema-modeled data warehouse ready for BI consumption.

![Azure Synapse](https://img.shields.io/badge/Azure%20Synapse-Analytics-0078D4?style=flat-square&logo=microsoftazure&logoColor=white)
![PySpark](https://img.shields.io/badge/PySpark-Engine-E25A1C?style=flat-square&logo=apachespark&logoColor=white)
![ADLS Gen2](https://img.shields.io/badge/ADLS-Gen2-0089D6?style=flat-square&logo=microsoftazure&logoColor=white)
![Dedicated SQL Pool](https://img.shields.io/badge/Synapse-Dedicated%20SQL%20Pool-336791?style=flat-square&logo=microsoftsqlserver&logoColor=white)
![Power BI](https://img.shields.io/badge/Power%20BI-Reporting-F2C811?style=flat-square&logo=powerbi&logoColor=black)
![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)

---

## 📖 Overview

This repository documents and implements the **Retail Transactions Medallion Data Pipeline**, engineered to ingest, cleanse, transform, and model high-volume daily retail transaction data into an optimized **dimensional Star Schema** for enterprise reporting and analytical exploration.

The pipeline strictly follows the **Medallion Architecture** paradigm, structuring data flow into three incremental quality layers — **Bronze**, **Silver**, and **Gold** — guaranteeing data lineage, auditability, and fully idempotent reprocessing.

> **Architectural Principle:** Ingestion bugs or business rule changes can be re-run at any time from the immutable Bronze layer, without ever needing to re-extract data from source operational systems.

---

## 🗂️ Table of Contents

- [Architecture Overview](#️-architecture-overview)
- [Storage Hierarchy & Folder Structure](#-storage-hierarchy--folder-structure)
- [Synapse PySpark Transformation Engine](#️-synapse-pyspark-transformation-engine)
- [Gold Layer: Star Schema Modeling](#-gold-layer-star-schema-dimensional-modeling)
- [Synapse Dedicated SQL Pool](#-synapse-dedicated-sql-pool-data-warehouse)
- [Data Quality & Governance Framework](#-automated-data-quality--governance-framework)
- [BI Analytics Catalog & Power BI Views](#-bi-analytics-catalog--power-bi-views)
- [Tech Stack](#-tech-stack)
- [License](#-license)

---

## 🏗️ Architecture Overview

```mermaid
flowchart LR
    A[Landing Zone\nCSV / Excel] --> B[Bronze Layer\nRaw Immutable History]
    B --> C[Silver Layer\nCleaned & Typed]
    C --> D[Gold Layer\nStar Schema]
    D --> E[Synapse Dedicated\nSQL Pool]
    E --> F[Power BI\nSemantic Views]

    style A fill:#f5deb3,color:#000
    style B fill:#cd7f32,color:#fff
    style C fill:#c0c0c0,color:#000
    style D fill:#ffd700,color:#000
    style E fill:#336791,color:#fff
    style F fill:#f2c811,color:#000
