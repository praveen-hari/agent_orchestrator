# Sprint & Task Templates (Agent-Friendly)

This repository contains lightweight **YAML/Markdown templates** for planning, tracking, and documenting work in an agent-assisted sprint (epics → tasks → results), plus optional agent role configs under `.codestudio/`.

## Repository layout

- `tasks/current-sprint.yaml` — sprint index (epics, milestones, tasks, session notes)
- `tasks/task-template.md` — detailed task template (intended for `tasks/task-details/task-XXX.md`)
- `tasks/requirements-template.md` — functional/non-functional requirements template
- `tasks/user-stories-template.md` — user stories template (with acceptance criteria)
- `tasks/agent-log-template.md` — chronological activity log template
- `.codestudio/agents/*.agent.md` — example agent role definitions (MainAgent, BackendTeammate, etc.)

## Recommended usage

1. Create a per-project folder (example):
   - `projects/<project-name>/{requirements,design,tasks,results}`
2. Copy templates into that folder and rename as needed:
   - `tasks/requirements-template.md` → `projects/<project-name>/requirements/requirements.md`
   - `tasks/user-stories-template.md` → `projects/<project-name>/requirements/user-stories.md`
   - `tasks/current-sprint.yaml` → `projects/<project-name>/tasks/current-sprint.yaml`
   - Use `tasks/task-template.md` to create `projects/<project-name>/tasks/task-details/task-XXX.md`
   - `tasks/agent-log-template.md` → `projects/<project-name>/results/agent-log.md`
3. Keep `current-sprint.yaml` as the fast, editable index; put full context in `task-details/`.

## Conventions

- **Task status:** `ready | blocked | claimed | in-progress | review | completed | failed`
- **Epic status:** `planned | in-progress | completed | blocked`
- Prefer small tasks (≤60 minutes); split larger tasks into subtasks/checkpoints.

