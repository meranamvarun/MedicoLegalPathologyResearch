# Data directory

The data directory separates unmodified source material from cleaned, coded, and analysis-ready datasets.

- `raw/cases/`: full-text judgments, orders, or permitted source documents saved exactly as retrieved.
- `raw/search_results/`: source search exports, result pages, snippets, and citation lists.
- `raw/literature/`: unmodified literature search exports, citation files, and legally permitted article files.
- `processed/`: screened, deduplicated, and coded case-level datasets.
- `processed/literature/`: screened and deduplicated literature-review records.
- `analysis/`: datasets generated for statistical and thematic analysis.
- `analysis/literature/`: literature synthesis datasets, citation-lead lists, and thematic extraction outputs.
- `metadata/`: templates and logs documenting provenance, search strategy, coding, literature screening, and audit trails.

Raw files should not be manually edited. If a correction is needed, document it in metadata and apply it through a script.
