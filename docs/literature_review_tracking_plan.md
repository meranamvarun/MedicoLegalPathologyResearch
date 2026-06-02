# Literature Review Tracking Plan

## 1. Purpose

The case-law review should be supported by a structured literature review so the study can document existing medico-legal, pathology, diagnostic-error, and Indian medical-negligence scholarship. Literature tracking will help identify background concepts, prior case discussions, legal principles, clinical standards, and secondary citations to additional judicial decisions.

## 2. Literature sources

Search both medical and legal scholarship sources because relevant commentary may appear outside conventional biomedical databases.

### Biomedical and public-health databases

1. PubMed/MEDLINE.
2. Google Scholar.
3. IndMED or other Indian biomedical indexes, where available.
4. Institutional library discovery tools.

### Legal and medico-legal sources

1. Law journal databases available through the institution.
2. Indian legal commentary databases and case-law platforms with article modules.
3. Bar, bench, and medico-legal professional publications.
4. References cited in retrieved judgments.
5. References cited in included review articles, case comments, and textbooks.

## 3. Suggested search concepts

Use combinations of pathology, diagnostic-error, legal, and India-specific concepts. Record every search in `data/metadata/literature_search_log_template.csv`.

### Pathology and diagnostic concepts

- pathology
- pathologist
- histopathology
- cytology
- FNAC
- laboratory medicine
- diagnostic error
- misdiagnosis
- delayed diagnosis
- specimen error
- reporting error
- diagnostic discrepancy

### Legal and medico-legal concepts

- medical negligence
- malpractice
- medico-legal
- consumer court
- deficiency in service
- expert evidence
- Bolam test
- standard of care
- liability
- compensation

### India-specific concepts

- India
- Indian case law
- Supreme Court of India
- High Court
- National Consumer Disputes Redressal Commission
- State Consumer Disputes Redressal Commission

## 4. Screening workflow

1. Export citation results into `data/raw/literature/` without manual editing.
2. Enter each record into `data/metadata/literature_inventory_template.csv`.
3. Screen titles and abstracts for relevance to pathology diagnostic error, medical negligence, Indian case law, diagnostic quality, or legal standards.
4. Retrieve full text where available and legally permitted.
5. Record full-text eligibility, exclusion reasons, and citation leads.
6. Extract relevant concepts into `data/metadata/literature_extraction_template.csv`.
7. Use citation chasing to identify additional judgments and add them to the case inventory when eligible.

## 5. Inclusion criteria

Include literature records if they meet at least one of the following criteria:

1. Discuss pathology, laboratory medicine, cytology, FNAC, histopathology, autopsy, or diagnostic error in a medico-legal context.
2. Discuss Indian medical negligence law, consumer forum decisions, or judicial tests relevant to diagnostic error.
3. Report or comment on Indian cases involving diagnostic error, laboratory reports, pathology reports, or autopsy evidence.
4. Provide clinical or quality-assurance guidance useful for interpreting pathology diagnostic error mechanisms.

## 6. Exclusion criteria

Exclude records if they are unrelated to diagnostic error, pathology/laboratory practice, Indian medical negligence, or general legal principles used in medical negligence analysis. Exclude inaccessible full-text records only after documenting reasonable retrieval attempts.

## 7. Extraction fields

For each included literature record, capture:

- citation identifier
- title
- authors
- year
- publication type
- source database
- URL or DOI
- country or jurisdiction focus
- relevance category
- key medico-legal principles discussed
- pathology or diagnostic-error concepts discussed
- Indian cases cited
- clinical standards or quality practices mentioned
- usefulness for background, methods, discussion, or recommendations
- reviewer notes

## 8. Outputs

The literature review should produce:

1. A tracked bibliography of included and excluded records.
2. A table of secondary sources that cite potentially eligible Indian cases.
3. A thematic summary of medico-legal principles and pathology risk-management recommendations.
4. A list of background sources for the final manuscript.
