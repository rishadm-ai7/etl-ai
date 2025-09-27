# etl-ai

## Overview
This project implements a data pipeline to extract, transform, and load Australian company data from:
1. **Common Crawl (March 2025 Index)** — extract company names, URLs, industries from ~200k AU websites.
2. **Australian Business Register (ABR)** — parse bulk XML files with official ABN, entity details, addresses.

The pipeline integrates both sources into a **unified company view** stored in PostgreSQL, with raw/curated data staged in a **data lake (MinIO, Parquet-Iceberg)** and queried using **Trino**.

---

## Architecture


---

## Tech Stack
- **Storage**: MinIO (S3-compatible, low-cost object storage)
- **SQL Query Engine**: Trino
- **Processing**: PySpark for parsing, normalization, feature generation
- **Data Modeling & Testing**: dbt
- **Database**: PostgreSQL (canonical unified view, indexes, permissions)
- **Entity Matching**:
  - Deterministic rules (ABN, domain, postcode)
  - ML features (fuzzy string, embeddings, ANN)
  - LLM for ambiguous cases (with JSON-structured prompts)

---

Using storage as MinIO initially because its not very good to store it in db osince the storage cost is very high and its not very optimal to store big data in dbs like postgres.