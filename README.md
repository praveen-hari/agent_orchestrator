# Task & Sprint Templates

Lightweight templates for capturing **requirements**, **user stories**, and an **implementation sprint plan** (epics + tasks) in a way that’s easy for humans and agents to scan and update.

## What’s in this repo

- `tasks/current-sprint.yaml` — sprint index (epics, milestones, and a compact task list)
- `tasks/task-details/` — per-task Markdown files with full context
- `tasks/task-template.md` — template for new task detail files
- `tasks/requirements-template.md` — functional + non-functional requirements template
- `tasks/user-stories-template.md` — user story template with acceptance criteria
- `tasks/agent-log-template.md` — chronological activity log template
- `.codestudio/agents/` — example agent role definitions (if you’re using CodeStudio/Codex-style multi-agent handoffs)

## Quick start

1. Copy the templates into your project folder (or keep using `tasks/` directly).
2. Fill out:
   - `tasks/requirements-template.md`
   - `tasks/user-stories-template.md`
3. Create or update `tasks/current-sprint.yaml` with your epics and task index entries.
4. For each task in the sprint index, create a matching detail file in `tasks/task-details/` using `tasks/task-template.md`.

## Conventions

- Keep `current-sprint.yaml` minimal and scan-friendly; put deep context in `task-details/*.md`.
- Use task `status` to manage dependencies (`blocked` → `ready` → `claimed` → `in-progress` → `review` → `completed`).
- Log major actions in an agent/activity log (see `tasks/agent-log-template.md`).

