# Data Collection Plan

## 1. Study scope

The study will collect reported Indian judicial decisions involving alleged pathology-related diagnostic errors and analyze them through combined legal and clinical review. Eligible matters may involve pathologists, pathology laboratories, hospital pathology departments, diagnostic centers, or autopsy/forensic pathology services.

## 2. Core data sources

Use a multi-source strategy because pathology-related litigation may be indexed inconsistently across legal databases and public repositories.

### Primary legal sources

1. Supreme Court of India judgments and orders.
2. High Court judgment portals and public case-law repositories.
3. National Consumer Disputes Redressal Commission decisions.
4. State Consumer Disputes Redressal Commission decisions where available.
5. District Consumer Disputes Redressal Commission decisions where available.
6. Indian legal databases available to the research team, such as SCC Online, Manupatra, Indian Kanoon, LiveLaw, or equivalent institutional subscriptions.

### Supplementary sources

1. Published medico-legal articles discussing Indian diagnostic-negligence cases.
2. Medical council or professional disciplinary decisions, if publicly available and relevant.
3. Hospital/laboratory accreditation and quality guidance used for contextual clinical interpretation.
4. Secondary citations from retrieved judgments and review articles tracked through `docs/literature_review_tracking_plan.md`.

## 3. Search strategy

Search each source with controlled combinations of legal, pathology, diagnostic, and harm/outcome terms. Searches should be logged in `data/metadata/search_log_template.csv`.

### Pathology terms

- pathology
- pathologist
- histopathology
- biopsy
- cytology
- FNAC
- fine needle aspiration
- Pap smear
- smear report
- laboratory report
- diagnostic laboratory
- clinical laboratory
- blood test
- autopsy
- post-mortem
- forensic pathology

### Diagnostic-error terms

- wrong diagnosis
- misdiagnosis
- delayed diagnosis
- erroneous report
- false positive
- false negative
- reporting delay
- specimen mix-up
- sample mix-up
- lost specimen
- inadequate sample
- communication failure
- negligent report

### Legal terms

- medical negligence
- deficiency in service
- consumer complaint
- compensation
- expert evidence
- standard of care
- Bolam
- res ipsa loquitur
- causation
- duty of care

## 4. Inclusion criteria

Include a decision if all criteria are satisfied:

1. The decision is from an Indian judicial or quasi-judicial forum.
2. The matter concerns alleged diagnostic error, reporting failure, specimen handling problem, or pathology/autopsy-related dispute.
3. The decision contains enough factual detail to classify the alleged pathology issue and outcome.
4. The case involves patient care, forensic/autopsy determination, or clinical decision-making influenced by pathology or laboratory evidence.

## 5. Exclusion criteria

Exclude a decision if any criterion applies:

1. The matter is about general hospital negligence without an identifiable pathology or laboratory diagnostic issue.
2. The reference to laboratory testing is incidental and not part of the negligence allegation or judicial reasoning.
3. The matter is a duplicate report of a case already included at a later or more authoritative appellate stage, unless both stages are needed for outcome tracking.
4. The document lacks sufficient detail after reasonable attempts to retrieve the full judgment.
5. The matter is non-Indian or only discusses foreign case law.

## 6. Case identification workflow

1. Run searches source by source using the configured strings.
2. Export search results, citations, URLs, snippets, and search dates into `data/raw/search_results/`.
3. Download or save full judgments into `data/raw/cases/` using stable filenames: `YEAR_FORUM_SHORTTITLE_CITATIONID.ext`.
4. Enter each candidate case into `data/metadata/case_inventory_template.csv`.
5. Conduct title/snippet screening for broad relevance.
6. Conduct full-text eligibility screening against inclusion and exclusion criteria.
7. Deduplicate by parties, citation, court/forum, decision date, and factual narrative.
8. Link appellate histories so trial/forum, appellate, and final decisions can be analyzed separately or as a single dispute unit.
9. Cross-check literature citation leads from `data/metadata/literature_extraction_template.csv` against the case inventory to identify cases missed by database searches.

## 7. Data extraction domains

### Bibliographic and procedural fields

- case identifier
- case name
- citation
- court or forum
- jurisdiction and state
- decision date
- procedural stage
- appeal status
- source database
- URL or source reference

### Clinical/pathology fields

- pathology domain: histopathology, cytology, FNAC, clinical laboratory, autopsy, other
- specimen type
- disease area: oncology, obstetrics/gynecology, infectious disease, hematology, forensic, other
- alleged error category
- alleged mechanism: interpretation, sampling, handling, reporting delay, communication, documentation, system failure
- harm alleged
- clinical outcome
- whether a second opinion or repeat test was involved
- whether discordance between reports was documented

### Legal fields

- claimant type
- defendant type
- legal cause of action
- forum outcome
- negligence finding
- deficiency in service finding
- causation finding
- compensation claimed
- compensation awarded
- costs or interest awarded
- expert evidence used
- legal principles cited
- court reasoning summary

### Reviewer judgment fields

- clinical reviewer assessment: likely negligence, system failure, diagnostic limitation, acceptable interpretation difference, unclear
- legal reviewer assessment: liability-supported, liability-not-supported, insufficient record, unclear
- quality-of-evidence rating
- notes on ambiguity

## 8. Coding approach

Use dual coding for legally and clinically complex fields. At minimum, one legally trained reviewer and one pathology/clinical reviewer should independently code each eligible case. Disagreements should be reconciled through consensus and documented in an audit trail.

Recommended coding levels:

1. **Screening code:** eligible, excluded, unclear.
2. **Error-type code:** histopathology, cytology, FNAC, delay, specimen handling, documentation, communication, autopsy, mixed, other.
3. **Outcome code:** plaintiff success, defendant success, partial success, remand, settlement/withdrawn, unclear.
4. **Negligence code:** negligence found, negligence not found, not decided, unclear.
5. **Clinical interpretation code:** negligent error, non-negligent diagnostic limitation, system/process failure, acceptable professional disagreement, unclear.

## 9. Quality control

1. Maintain case-law and literature search logs with source, query, filters, date searched, and number of hits.
2. Preserve raw search exports and raw judgments without manual editing.
3. Use a case inventory to track provenance, screening decisions, and deduplication decisions.
4. Apply duplicate checks using normalized party names, decision dates, citations, and forum names.
5. Re-code a sample of cases to estimate inter-reviewer agreement.
6. Document all exclusion reasons.
7. Keep analysis-ready datasets separate from raw and processed data.

## 10. Planned analyses

1. Frequency of cases by year, forum, state, and pathology domain.
2. Distribution of alleged error categories.
3. Litigation outcome proportions overall and by forum.
4. Compensation summaries, including median, range, and inflation-adjusted sensitivity analysis if appropriate.
5. Cross-tabulation of liability findings by expert evidence, documentation quality, delay, communication failure, and repeat-test discordance.
6. Thematic analysis of legal principles, including Bolam, duty of care, causation, expert testimony, and error of judgment.
7. Clinical synthesis distinguishing negligence from diagnostic limitations and system failures.

## 11. Ethical and legal considerations

The dataset should rely on publicly available legal decisions or institutionally licensed databases used within their terms. Avoid publishing unnecessary personal identifiers beyond what is already essential in public legal citations. Store subscription-source exports according to license restrictions and do not redistribute restricted full-text documents unless permitted.
