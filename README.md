# Medico-Legal Pathology Research

This repository supports the study **"Diagnostic Errors in Pathology and Their Medico-Legal Consequences: A Mixed Legal and Clinical Review of Indian Case Law."** It is organized to keep legal case retrieval, clinical/legal coding, analysis code, and study outputs reproducible and auditable.

## Repository layout

| Path | Purpose |
| --- | --- |
| `docs/` | Full study protocol, data collection plan, literature review tracking plan, coding rules, and documentation. |
| `config/` | Search terms, source lists, literature strategies, and other configurable collection settings. |
| `data/raw/` | Unmodified source material, including downloaded judgments, case search exports, and literature exports. |
| `data/processed/` | Cleaned case-level datasets after screening, deduplication, and coding. |
| `data/analysis/` | Analysis-ready datasets generated from processed data. |
| `data/metadata/` | Data dictionaries, case and literature inventories, provenance logs, source inventories, and audit files. |
| `code/collectors/` | Scripts for case-law search, download, citation extraction, and metadata capture. |
| `code/cleaning/` | Scripts for deduplication, eligibility screening, and dataset harmonization. |
| `code/analysis/` | Scripts for descriptive statistics, outcome summaries, and legal/clinical theme analysis. |
| `code/utils/` | Shared helper functions used by collection, cleaning, and analysis scripts. |
| `notebooks/` | Exploratory notebooks for legal mapping, clinical review, and interim analysis. |
| `outputs/` | Tables, figures, reports, and manuscript-ready exports. |
| `tests/` | Lightweight tests for parsing, cleaning, and coding utilities. |

## Recommended workflow

1. Start from the full protocol in `docs/study_protocol.md`, then configure case-law sources and search strings in `config/search_strategy.yml`, and literature sources in `config/literature_search_strategy.yml`.
2. Store source exports, downloaded judgments, and literature citation exports in `data/raw/` without manual editing.
3. Record provenance for every case in `data/metadata/case_inventory_template.csv` and every literature record in `data/metadata/literature_inventory_template.csv`.
4. Screen and deduplicate cases using scripts in `code/cleaning/`.
5. Apply legal and clinical coding fields described in `docs/data_collection_plan.md`, and track literature review decisions using `docs/literature_review_tracking_plan.md`.
6. Generate analysis-ready datasets in `data/analysis/` and outputs in `outputs/`.
