---
name: medico-legal-pathology-research
description: >
  Project-specific academic research workflow for the MedicoLegalPathologyResearch repository. Use when working on diagnostic errors in pathology and medico-legal consequences in Indian case law, including case-law retrieval, literature review, PRISMA-style screening, clinical/legal coding, source verification, mixed legal-clinical synthesis, manuscript drafting, revision, citation checks, and peer-review readiness. Adapted from the relevant Academic Research Skills workflows: deep-research, academic-paper, academic-paper-reviewer, and academic-pipeline.
---

# Medico-Legal Pathology Research Skill

Use this skill for repository work supporting **Diagnostic Errors in Pathology and Their Medico-Legal Consequences: A Mixed Legal and Clinical Review of Indian Case Law**.

This skill is intentionally packaged as a single neutral `SKILL.md` with only `name` and `description` frontmatter so it remains compatible with both Codex skill discovery and Claude Code project-skill discovery. It adapts only the relevant Academic Research Skills workflows for this project instead of vendoring the full upstream suite.

## Source And Attribution

Based on Academic Research Skills by Cheng-I Wu: <https://github.com/Imbad0202/academic-research-skills>.

Relevant upstream workflows considered:

- `deep-research` for literature review, systematic review, fact-checking, Socratic research-question refinement, and evidence synthesis.
- `academic-paper` for manuscript planning, drafting, revision, citation checking, formatting, and disclosure support.
- `academic-paper-reviewer` for structured peer-review simulation and methodology-focused critique.
- `academic-pipeline` for staged research-to-paper orchestration with integrity gates.

Not copied as standalone upstream skills because their native files use Claude-specific agent-team routing, slash commands, hooks, and cross-file assumptions. This project skill preserves the relevant workflow ideas in a portable Codex/Claude Code format.

## Repository Context

Read these project files before substantive work:

1. `README.md` for repository layout and workflow.
2. `docs/study_protocol.md` for research question, inclusion/exclusion criteria, variables, reviewer process, and analysis plan.
3. `docs/data_collection_plan.md` for case inventory, clinical/legal coding, and audit expectations.
4. `docs/literature_review_tracking_plan.md` for literature-screening provenance.
5. `config/search_strategy.yml` for case-law sources and search strings.
6. `config/literature_search_strategy.yml` for academic literature sources and search strings.

Treat `data/raw/` as immutable source material. Record provenance for every case, export, search, coding decision, and exclusion.

## Workflow Router

Select one workflow by the user's immediate goal:

| User goal | Workflow | Primary output |
| --- | --- | --- |
| Clarify broad topic, refine research question, or scope searches | `research-scoping` | Candidate research questions, FINER-style feasibility notes, search boundaries |
| Build or revise case-law and literature searches | `search-strategy` | Search strings, source list, search log fields, inclusion/exclusion plan |
| Screen cases or articles | `screening` | Eligibility decisions with reasons and audit trail |
| Extract or code legal/clinical variables | `coding` | Completed coding fields, ambiguity notes, dual-review flags |
| Verify citations, judgments, claims, dates, or compensation figures | `verification` | Source-backed verification table with uncertainty labels |
| Synthesize findings | `synthesis` | Clinical/legal themes, contradiction map, evidence-quality caveats |
| Draft manuscript/report sections | `writing` | Structured outline or section draft aligned with protocol |
| Review a draft, table, coding schema, or methodology | `review` | Reviewer-style critique and revision priorities |
| Manage a full research-to-paper run | `pipeline` | Stage dashboard, completed artifacts, next gate |

If the request spans multiple workflows, start with `pipeline` unless the user explicitly asks for a single phase.

## Operating Rules

1. **Verify unstable or external facts.** Browse or otherwise verify current case-law, database coverage, source URLs, article metadata, legal status, journal requirements, and citation details. Cite sources when reporting external facts.
2. **Separate evidence from inference.** Label statements as `source-supported`, `reviewer interpretation`, `unclear`, or `unverified` when coding or synthesizing.
3. **Preserve legal nuance.** Do not treat every diagnostic error as negligence. Distinguish alleged error, proved breach, causation, deficiency in service, compensation, and appellate posture.
4. **Preserve clinical nuance.** Distinguish histopathology, cytology, FNAC, laboratory diagnostics, autopsy/post-mortem issues, specimen handling, reporting delay, communication failure, and acceptable professional disagreement.
5. **Avoid unauthorized legal or medical advice.** Provide research support, not legal representation or clinical recommendations for a real patient.
6. **Respect source integrity.** Do not rewrite raw judgments, raw literature exports, or downloaded source files. Store transformations under `data/processed/`, `data/analysis/`, or documented outputs.
7. **Use dual-review flags.** Mark legally or clinically ambiguous items for legal and pathology/clinical reviewer reconciliation.
8. **Maintain auditability.** Every search, exclusion, coding change, and synthesis claim should be traceable to source material or a documented reviewer decision.

## Workflow Details

### `research-scoping`

Use when the project question, subquestions, or scope boundaries need refinement.

Steps:

1. Restate the current research objective from `docs/study_protocol.md`.
2. Identify the specific uncertainty: population, pathology domain, forum, timeframe, legal doctrine, outcome, or evidence source.
3. Propose 2-3 focused subquestions and score each for feasibility, relevance, novelty, and auditability.
4. Ask focused clarification questions only when required to prevent wrong downstream work.
5. Produce scope boundaries: in-scope, out-of-scope, edge cases, and required source types.

### `search-strategy`

Use when building, expanding, or auditing searches.

Steps:

1. Start from `config/search_strategy.yml` for case law and `config/literature_search_strategy.yml` for scholarship.
2. Combine pathology terms, error terms, legal terms, and jurisdiction/forum terms.
3. Preserve exact queries and database/source names for search logs.
4. Include synonyms and spelling variants: `medico-legal`, `medicolegal`, `FNAC`, `fine needle aspiration`, `histopathology`, `cytology`, `biopsy`, `post-mortem`, and `deficiency in service`.
5. Produce a table with source, query, filters, date run, expected export path, and notes.

### `screening`

Use when deciding whether a judgment, complaint, article, or abstract belongs in the study.

Steps:

1. Apply protocol inclusion/exclusion criteria exactly.
2. Assign one status: `eligible`, `excluded`, or `unclear`.
3. For exclusions, record a concise reason tied to the protocol.
4. Flag edge cases for dual review, especially mixed specialties, laboratory-administration claims, unclear pathology role, or appellate decisions with limited facts.
5. Preserve source identifiers and file paths.

### `coding`

Use for case-level legal and clinical extraction.

Steps:

1. Extract bibliographic/procedural fields first: case name, citation, forum, jurisdiction, date, source, URL/reference, raw path, and appeal status.
2. Extract clinical/pathology variables: domain, specimen type, disease area, alleged error category, alleged mechanism, harm, clinical outcome, repeat test/second opinion, and report discordance.
3. Extract legal variables: claimant, defendant, cause of action, forum outcome, negligence finding, deficiency finding, causation, compensation claimed/awarded, costs/interest, expert evidence, principles cited, and reasoning summary.
4. Add reviewer assessment fields: clinical assessment, legal assessment, documentation quality, evidence quality, ambiguity notes.
5. Use controlled terms from the protocol where available; otherwise add `other` plus a note.

### `verification`

Use for citation, case, legal, medical, or manuscript integrity checks.

Steps:

1. Verify primary sources first: official court/commission portals, published judgment text, DOI/Crossref/PubMed/official journal pages, or archived source exports.
2. Record exact source location or URL and access date when relevant.
3. Check dates, parties, forum, appellate history, negligence findings, compensation amounts, and quoted legal principles against the source.
4. For literature, verify that a cited source exists and supports the claim being made.
5. Produce a table: claim/field, source checked, verdict (`verified`, `partly verified`, `not verified`, `conflicting`, `unavailable`), correction, and notes.

### `synthesis`

Use for combining coded legal and clinical findings.

Steps:

1. Separate descriptive summaries from interpretive themes.
2. Map findings by forum, year, pathology domain, alleged error type, legal principle, expert evidence, outcome, and compensation.
3. Identify contradictions, sparse evidence, reporting bias, and missing data.
4. Avoid overgeneralizing from case law; court decisions reflect litigated disputes, not incidence of diagnostic error.
5. Produce clinically and legally cautious interpretations with limitations.

### `writing`

Use for outlines, manuscript sections, abstracts, tables, figures, responses to reviewers, or final reports.

Steps:

1. Align structure with the study protocol and the target output: protocol update, methods, results, discussion, manuscript, conference abstract, or policy brief.
2. Keep claims traceable to coded data, source documents, or literature.
3. Use citation placeholders when exact references are not verified; do not invent citations.
4. Include AI-assistance disclosure language when requested or required by the venue.
5. Mark gaps that require human legal/pathology review before submission.

### `review`

Use for peer-review style evaluation of drafts, methods, coding templates, or outputs.

Steps:

1. Review from three perspectives: legal-methods reviewer, pathology/clinical reviewer, and evidence-synthesis reviewer.
2. Score or categorize issues by severity: `critical`, `major`, `minor`, or `suggestion`.
3. Preserve strong criticism; do not soften methodological or citation-integrity problems in the final synthesis.
4. Provide a revision priority list and concrete next actions.

### `pipeline`

Use for multi-stage orchestration.

Stages:

1. Intake and scope confirmation.
2. Case-law and literature search strategy.
3. Retrieval and provenance logging.
4. Screening and deduplication.
5. Legal/clinical coding.
6. Verification and integrity gate.
7. Descriptive and thematic synthesis.
8. Manuscript/report drafting.
9. Structured review and revision.
10. Final integrity check and output packaging.

At each stage, report completed artifacts, unresolved blockers, required human review, and the next recommended stage.

## Output Defaults

- Use English unless the user requests another language.
- Prefer tables for coding, screening, verification, and search logs.
- Include file paths for repository artifacts.
- Cite repository files when explaining project-specific requirements.
- When external verification was not performed or failed, state that clearly.
