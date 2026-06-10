# Phase 2 Plan: Case-Law Identification, Screening, and Inventory Build

## Status of the Project

Phase 1 (protocol and literature survey) is complete:

- Full study protocol, data collection plan, and literature tracking plan are in `docs/`.
- 68 literature sources identified across six domains, logged in
  `data/metadata/literature_inventory_template.csv` with 23 searches in the
  literature search log.
- Structured extraction completed and a narrative literature review drafted in
  `outputs/literature/literature_review_draft.md`.
- PRISMA flow tracked in `outputs/literature/prisma_flow.csv`; full-text
  screening and citation chasing remain open items carried into this phase.

The case-law side — the primary unit of analysis for this study — has not yet
started: `case_inventory_template.csv`, `search_log_template.csv`, and
`coding_template.csv` contain headers only, and `code/` contains no scripts.

## Phase 2 Objective

Build the complete, deduplicated, screened inventory of candidate Indian
judicial and quasi-judicial decisions involving alleged pathology-related
diagnostic errors, with full provenance, so that Phase 3 (dual coding and
extraction) can begin on a stable case set.

## Workstreams

### Workstream 1 — Execute the case-law search strategy

Run the query matrix defined in `config/search_strategy.yml` against each
configured source, in priority order:

1. **National Consumer Disputes Redressal Commission (NCDRC)** — highest
   expected yield; the literature survey (Domain C/F sources) confirms most
   pathology negligence disputes are consumer matters.
2. **Supreme Court of India** — judgments and orders portal.
3. **High Courts** — via public aggregators (e.g. Indian Kanoon, eCourts),
   jurisdiction by jurisdiction.
4. **State Consumer Commissions** — where public search access exists.
5. **Legal databases** (SCC Online / Manupatra or equivalent, if
   institutionally licensed) — within license terms; do not redistribute raw
   exports if prohibited.

Operating rules:

- Log **every** executed query in `data/metadata/search_log_template.csv`
  (search_id, date, source, query, filters, hits, export path, searcher),
  including zero-hit queries.
- Save raw search exports to `data/raw/search_results/` and full judgment
  texts to `data/raw/cases/` using stable, descriptive filenames
  (e.g. `NCDRC_2014_<party>_v_<party>.pdf`); never edit raw files.
- Seed the search with the **known cases already identified in the literature
  survey** (Domain B landmark cases and Domain C pathology-specific cases) —
  enter them in the case inventory immediately with `source_database =
  literature_citation`.

### Workstream 2 — Populate the case inventory and screen

- Enter every candidate decision in
  `data/metadata/case_inventory_template.csv` with a stable `case_id`
  (suggested scheme: `IND-PATH-0001` onward, assigned at first entry).
- **Title/snippet screening:** mark `screening_status` as
  eligible / excluded / unclear against protocol §11; record
  `exclusion_reason` for every exclusion.
- **Full-text screening:** retrieve full judgments for all
  eligible-or-unclear records; apply inclusion criteria 11.1.3 (sufficient
  factual detail) only after retrieval attempts are documented in `notes`.
- Per protocol §14, screening decisions on borderline records should be
  dual-reviewed; log disagreements and resolutions in the notes/audit fields.

### Workstream 3 — Deduplicate and link appellate histories

- Deduplicate on party names, citation, decision date, forum, and factual
  narrative; assign a shared `duplicate_group_id` rather than deleting rows.
- Where one dispute spans multiple forums (District → State → NCDRC →
  Supreme Court), keep each decision as its own row and link them with a
  common `appellate_history_id` so dispute-level analysis is possible later.

### Workstream 4 — Close out the literature review loose ends

Carried over from Phase 1, per `outputs/literature/prisma_flow.csv`:

1. Complete full-text retrieval and eligibility assessment for the 67
   deduplicated literature records; update the
   `full_text_assessed_for_eligibility` and `full_text_excluded_with_reasons`
   PRISMA rows.
2. Extract **cited Indian cases** from each eligible source (citation
   chasing) and reconcile them against the case inventory; new leads enter
   Workstream 2 with `source_database = literature_citation`.
3. Update `additional_records_from_citation_chasing` in the PRISMA tracker
   and revise the literature review draft if full-text review changes any
   characterization.

### Workstream 5 — Tooling and validation scripts

Stand up the minimum code needed to keep the inventory auditable, in line
with the repository layout:

- `code/utils/` — shared CSV schema definitions matching the metadata
  templates.
- `code/collectors/` — a script to validate and append search-log entries,
  and (where a source permits programmatic access) helpers to capture
  metadata for downloaded judgments.
- `code/cleaning/` — scripts to (a) validate the case inventory (unique IDs,
  required fields, controlled vocabulary for `screening_status` and
  `forum`), (b) flag candidate duplicates by fuzzy party-name/date matching,
  and (c) emit a screening-status summary.
- `tests/` — unit tests for the validators and the duplicate-flagging logic.

Keep tooling lightweight: Python standard library plus `pandas` at most; no
scraping of sources whose terms prohibit it.

## Sequencing and Milestones

| Step | Milestone | Exit criterion |
|------|-----------|----------------|
| 2.1 | Seed inventory from literature-cited cases | All Domain B/C cases entered with provenance |
| 2.2 | NCDRC + Supreme Court searches executed | Search log complete for both sources; exports saved |
| 2.3 | High Court / State Commission / database searches executed | Search log complete for remaining sources |
| 2.4 | Title/snippet screening complete | Every inventory row has a screening_status |
| 2.5 | Full-text retrieval and eligibility screening complete | Every eligible row has a raw_file_path or documented retrieval failure |
| 2.6 | Deduplication and appellate linking complete | duplicate_group_id / appellate_history_id assigned; validator passes |
| 2.7 | Literature full-text review + citation chasing complete | PRISMA tracker has no pending rows |
| 2.8 | Phase 2 report | Screening summary (counts by source, forum, status) written to `outputs/reports/` |

Steps 2.1–2.3 can run in parallel with Workstream 5 (tooling); screening
(2.4–2.5) should not start at scale until the inventory validator exists.

## Deliverables

1. Fully populated `case_inventory_template.csv` with screening decisions and
   provenance for every candidate case.
2. Complete `search_log_template.csv` covering all sources and queries.
3. Raw judgments and search exports preserved under `data/raw/`.
4. Updated literature PRISMA tracker with full-text screening complete and
   citation-chasing yield recorded.
5. Validation/dedup scripts in `code/` with passing tests.
6. A Phase 2 screening report in `outputs/reports/` (counts identified,
   screened, excluded with reasons, eligible — the case-law analogue of the
   PRISMA flow), which becomes the case-flow diagram for the manuscript.

## Risks and Mitigations

- **Inconsistent indexing of consumer-forum decisions:** older State/District
  Commission decisions may be unsearchable. Mitigate via citation chasing
  from appellate decisions and literature (Workstream 4), and document
  coverage limits in the Phase 2 report.
- **Pathology issues buried in general negligence cases:** broad queries will
  return high-noise results. Keep recall high at title screening (exclude
  conservatively) and rely on full-text screening for precision.
- **License constraints on subscription databases:** store only
  license-compliant exports; record citations and metadata in the inventory
  even where full text cannot be archived.
- **Volume uncertainty:** if eligible cases exceed practical full-text
  capacity, document any sampling decision as a protocol amendment per §16.8
  before applying it.

## Out of Scope for Phase 2

Legal/clinical dual coding of eligible cases (`coding_template.csv`),
descriptive statistics, and thematic synthesis are Phase 3 and later. Phase 2
ends when the eligible case set is frozen and validated.
