# Repo Layout

This repository is intentionally small and focuses on task/workflow artifacts.

## Top-level

- `.codestudio/` — agent role definitions and handoff prompts
- `tasks/` — sprint index, task details, and templates
- `mkdocs.yml` — MkDocs configuration
- `docs/` — documentation source files (this site)
- `requirements-docs.txt` — Python deps to build docs

## Key paths

- Sprint index: `tasks/current-sprint.yaml`
- Task detail docs: `tasks/task-details/`
- Templates:
  - `tasks/task-template.md`
  - `tasks/requirements-template.md`
  - `tasks/user-stories-template.md`
  - `tasks/agent-log-template.md`
