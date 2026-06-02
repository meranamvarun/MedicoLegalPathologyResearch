# Code directory

Use this directory for reproducible scripts that transform raw case-law material into coded datasets and outputs.

- `collectors/`: source-specific search, download, and metadata-capture scripts.
- `cleaning/`: screening, deduplication, and harmonization scripts.
- `analysis/`: descriptive statistics, legal outcome analysis, and clinical/legal theme summaries.
- `utils/`: shared parsing, normalization, and validation helpers.

Scripts should read from `data/raw/` or `data/processed/` and write derived files to `data/processed/`, `data/analysis/`, or `outputs/`. Do not overwrite raw judgments or raw search exports.
