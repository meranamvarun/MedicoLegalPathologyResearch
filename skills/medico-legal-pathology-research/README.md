# Medico-Legal Pathology Research Skill

This project skill adapts the relevant workflows from [Academic Research Skills](https://github.com/Imbad0202/academic-research-skills) for the repository's mixed legal and clinical review of Indian pathology diagnostic-error case law.

## Compatibility

- **Codex:** discoverable as a standard `SKILL.md` folder and includes optional `agents/openai.yaml` UI metadata.
- **Claude Code:** uses a simple project-skill layout and avoids Codex-only frontmatter requirements in `SKILL.md`.

## Why this is a project-specific adaptation

The upstream repository contains broad Claude Code skills for deep research, paper writing, paper review, and full academic pipelines. For this repository, the relevant requirements are narrower: source provenance, case-law/literature searching, screening, legal and clinical coding, verification, synthesis, writing, and review. This folder therefore vendors the workflow concepts in a portable project skill rather than copying Claude-specific hooks, slash commands, and agent-team runtime assumptions.
