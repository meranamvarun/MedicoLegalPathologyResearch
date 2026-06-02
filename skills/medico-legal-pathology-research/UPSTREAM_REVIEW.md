# Upstream Academic Research Skills Review

Source reviewed: <https://github.com/Imbad0202/academic-research-skills>

## Relevant to this project and incorporated

| Upstream skill | Relevance | How incorporated |
| --- | --- | --- |
| `deep-research` | Literature review, systematic review, PRISMA-style screening, research-question refinement, fact-checking, source verification, synthesis. | Adapted into `research-scoping`, `search-strategy`, `screening`, `verification`, and `synthesis` workflows in `SKILL.md`. |
| `academic-paper` | Manuscript outlining, drafting, revision, citation checks, formatting, and disclosure. | Adapted into the `writing` workflow in `SKILL.md`. |
| `academic-paper-reviewer` | Methodology-focused critique, simulated peer review, editorial synthesis, and revision priorities. | Adapted into the `review` workflow in `SKILL.md`. |
| `academic-pipeline` | End-to-end staged research-to-paper management with integrity gates. | Adapted into the `pipeline` workflow in `SKILL.md`. |

## Not incorporated

| Upstream component | Reason |
| --- | --- |
| `experiment-agent` / experiment workflows | The repository is a legal/clinical evidence review, not a code-experiment or human-subjects experiment project. |
| Claude slash commands and hook metadata | Not portable across Codex and Claude Code without runtime-specific installation. |
| Full upstream agent and reference tree | Too broad for this project and includes Claude-specific routing assumptions; the project needs a narrower skill focused on case-law/literature provenance and mixed legal-clinical coding. |

## Items that would require discussion before adding

These upstream files could be useful with project-specific modification, but should be discussed before vendoring because they would add maintenance burden and may need tailoring to Indian medico-legal/pathology terminology:

1. Full `deep-research` systematic-review references and templates for a PRISMA-style literature appendix.
2. `academic-paper` citation-format and journal-format references if the target journal or citation style is selected.
3. `academic-paper-reviewer` rubric files if the team wants formal 0-100 scoring for internal review.
4. `academic-pipeline` material-passport schemas if the project wants a stricter machine-readable artifact ledger.
