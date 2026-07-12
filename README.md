# Azure Data Lakehouse Pipeline

> Production-style Azure Databricks and PySpark pipeline demonstrating Bronze, Silver, and Gold data layers with data-quality controls.

## Architecture

```text
CSV source -> Bronze (raw Delta) -> Silver (clean Delta) -> Gold (daily metrics)
                         |                    |
                         +-> quality checks ---+-> audit-ready data products
```

## Engineering highlights

- **Medallion architecture:** Bronze, Silver, and Gold Delta Lake layers.
- **Data quality:** required-field, duplicate-order, and non-negative amount validation.
- **Analytics:** daily revenue, order count, customer count, and average order value.
- **Cloud ready:** local configuration designed to move to Azure Databricks and ADLS Gen2.

## Technology stack

PySpark | Delta Lake | Azure Databricks | ADLS Gen2 | Python | Azure Data Factory | CI/CD

## Pipeline flow

1. Ingest order events and attach source-file and ingestion-time metadata.
2. Clean types, normalize values, remove duplicates, and enforce quality gates.
3. Aggregate curated orders into a daily analytics table.
4. Publish the Gold layer to support BI, reporting, and downstream AI workloads.

## Data quality gates

| Check | Purpose |
| --- | --- |
| Required fields | Prevent incomplete order records from entering Silver. |
| Unique order ID | Protect against duplicate transactions. |
| Non-negative amount | Detect invalid financial values early. |
| Schema validation | Ensure expected input columns are present. |

## Azure production path

- Store raw and curated layers in **ADLS Gen2**.
- Run the pipeline in **Azure Databricks**.
- Orchestrate with **Azure Data Factory** or Databricks Workflows.
- Use **Unity Catalog**, managed identities, and Azure Monitor for governance and observability.

## Local project structure

```text
src/        pipeline code for Bronze, Silver, Gold, and quality checks
tests/      validation tests
data/       sample order data
docs/       architecture and production-hardening notes
```

## Portfolio value

This project demonstrates practical data-engineering skills: distributed processing, lakehouse design, data quality, cloud architecture, and production-minded documentation.
