# Business Intelligence for LinkedIn Job Insights

## Overview
This repository documents and packages a Business Intelligence (BI) initiative centered on analyzing LinkedIn job postings to support recruiters, job seekers, and strategic planners with data-driven decision-making. The project culminates in a Power BI dashboard and a companion presentation that explain the approach, governance, and the value delivered.

## Features
- **Interactive Power BI Dashboard**
  - Role-based pages for recruiters and job seekers.
  - Drill-through and cross-filtering across locations, titles, industries, and seniority.
  - KPI cards (open roles, median salary, time-to-fill proxies, posting velocity).
  - Trend, distribution, and heatmap visuals for temporal and geographic analysis.
- **Robust Data Modeling**
  - Star-schema model with clearly defined dimensions (Job, Company, Location, Time) and fact tables.
  - Calculated columns and measures implemented in DAX for accuracy and reuse.
- **Data Integration & Preparation**
  - Power Query (M) pipelines for ingestion, cleaning (null handling, type casting), deduplication, and normalization.
  - Parameterized queries for environment portability (local vs. service).
- **Decision Support**
  - Scenario views to identify skill gaps and high-demand titles.
  - Benchmarks and thresholds for alerting on unusual spikes or drops in postings.
- **Performance Optimizations**
  - Measure simplification and variable use in DAX.
  - Aggregations and query folding where applicable.
  - Incremental refresh design guidance for service deployment.

## Security
- **Data Protection**
  - Strict handling of any sensitive or personally identifiable data (PII) with masking and exclusion in Power Query.
  - Source credentials stored securely (Windows/Organizational account), never in plain text.
- **Access Control**
  - Role Level Security (RLS) patterns to ensure users only view relevant slices (e.g., region/team).
  - Separate workspace roles for viewers, contributors, and admins in the Power BI Service.
- **Compliance & Governance**
  - Alignment with regulatory frameworks (GDPR/CCPA where applicable).
  - Dataset certification process and usage monitoring via Power BI lineage and audit logs.
- **Operational Continuity**
  - Defined refresh failure playbooks and notification policies.
  - Versioning of .pbix and documented change logs for reproducibility.

## Testing
- **Data Quality Checks**
  - Row-count and schema validation after each Power Query stage.
  - Referential integrity checks between fact and dimensions.
- **Measure & Logic Verification**
  - Sanity tests for DAX measures against hand-calculated samples.
  - Edge-case scenarios (e.g., missing salary, multi-location postings).
- **Performance Testing**
  - Use of Performance Analyzer to identify slow visuals/measures.
  - Cache behavior observations and cold vs. warm load comparisons.
- **Refresh & Deployment Tests**
  - Trial refresh in a staging workspace before production.
  - Parameter swap tests and gateway validation (if on-prem sources are used).

## Documentation & Analysis
- **Problem Framing**
  - Which roles are in demand, where, and how trends are evolving over time.
  - What skills correlate with higher posting frequency and potential salary bands.
- **Analytical Approach**
  - Cohort-like analysis by posting date to understand hiring cycles.
  - Outlier detection for anomalous spikes in postings by title or region.
- **User Guidance**
  - How-to navigation notes embedded in the report (tooltips, info icons).
  - FAQs for data freshness, definitions (e.g., “open roles”), and known caveats.
- **Presentation Materials**
  - An executive-friendly slide deck summarizing BI fundamentals, Power BI capabilities, dashboard walkthrough, benefits, and governance model.

## Technologies Used
- **Power BI Desktop / Service** for modeling, DAX, and interactive visualization.
- **Power Query (M)** for ETL (ingest, clean, transform).
- **DAX** for reusable measures and business logic.
- **Tabular Model (VertiPaq)** for in-memory analytics.
- **Excel/CSV/External Job Data Sources** as inputs (schema documented in repo notes).

## How to Run
```bash
# 1) Open the .pbix in Power BI Desktop
# 2) Update Parameters (e.g., file paths / environments)
# 3) Refresh preview; verify schema and sample outputs
# 4) Publish to the Power BI Service (staging first, then production)
# 5) Configure scheduled refresh and gateway (if required)
# 6) Assign workspace roles and, if used, RLS roles
