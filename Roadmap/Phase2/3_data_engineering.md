# Data ingestion and transformation

First principle: an AI system cannot produce reliable results from data that is missing, stale, inconsistent or incorrectly interpreted.

Learn:
- CSV, JSON, Parquet and relational data.
- Batch processing versus streaming.
- ETL versus ELT.
- Data profiling, schema validation and missing-value handling.
- Idempotency: safely retrying a job without duplicating its effects.
- Incremental processing, checkpoints and retries.
- Data lineage and source-of-truth identification.

Understand the architecture:

```mermaid
flowchart LR
    A[Client systems] --> B[Bronze: raw data]
    B --> C[Silver: cleaned data]
    C --> D[Gold: business-ready data]
    D --> E[Dashboard / AI / APIs]
```

Hands-on lab: 

ingest customer and ticket CSV files containing duplicate IDs, inconsistent timestamps, missing values and changing column names.

Build a pipeline that:

- Preserves the original input.
- Reports data-quality problems.
- Cleans and normalizes records.
- Creates business-ready tables.
- Can be rerun safely.
- Produces a clear failure report when validation fails.

Tools: Python, Pandas or Polars, DuckDB, PostgreSQL.