# Standard Teammate Workflow

Shared 5-step protocol for **BackendTeammate**, **FrontendTeammate**, and **TestingTeammate**.

**Workflow:** Claim → Execute → Document → Update → Handoff

All paths are relative to the active project folder `projects/{project-name}/`:

| File | Purpose |
|------|---------|
| `tasks/current-sprint.yaml` | Sprint index (epics, task status, dependencies) |
| `tasks/task-details/task-{ID}.md` | Full task context, subtasks, checkpoints, work log |
| `tasks/agent-log.md` | Chronological activity log (format: `tasks/agent-log-template.md` at repo root) |
| `requirements/`, `design/` | Requirements and specs to follow |
| `results/task-{ID}-result.md` | Result document for each completed task |

---

## Step 1: Claim

1. Read `tasks/current-sprint.yaml`.
2. Pick the highest `priority_score` task where `status: ready` and `type` matches your role (`backend` | `frontend` | `testing`).
3. Confirm every task in `dependencies` is `completed`. If not, leave it and pick another.
4. Update the task in YAML: `status: claimed`, `assigned_to: <YourAgentName>`.
5. Append a log entry to `tasks/agent-log.md` (`ready → claimed`, estimated duration).

## Step 2: Execute

1. Read `detail_file` (`tasks/task-details/task-{ID}.md`) and the specs it references in `design/` and `requirements/`.
2. Set `status: in-progress` in YAML and log `claimed → in-progress`.
3. Implement only what the task describes (files to create/modify, acceptance criteria).
4. For tasks with subtasks or `is_long_running: true`:
   - Tick subtask checkboxes as you finish them.
   - Mark checkpoints with timestamps so work can resume after interruption.
   - Add a work log session entry in the task markdown file.
5. Verify your work against each acceptance criterion (run code, tests, or manual checks).

If you are blocked, set `status: blocked` (external dependency) or `failed` (attempted, errored), record the reason in the task file's **Issues & Notes** and metadata `error` field, log it, and hand off to MainAgent.

## Step 3: Document

Create `results/task-{ID}-result.md` with:

- Summary of what was done
- Files created/modified
- Acceptance criteria checklist with results
- Code examples, test output, or screenshots (UI changes)
- Known issues, follow-ups, and recommendations
- **TestingTeammate:** pass/fail counts, coverage, and bugs in the bug report format

## Step 4: Update

1. In `tasks/current-sprint.yaml`:
   - Set task `status` (`completed`, or `review` if it needs review / bugs were found).
   - Set `actual_duration`.
   - Update epic `completed_tasks` and `progress = (completed_tasks / total_tasks) * 100`.
   - Update `metadata` counts (`completed_count`, `in_progress_count`, `ready_count`, etc.).
2. In the task markdown file: update status line, timeline, and **Result File** link; set metadata `updated_at`.
3. Append a completion entry to `tasks/agent-log.md` (status change, duration vs estimate, result file, summary).

MainAgent is responsible for unblocking dependent tasks; note in your log entry which tasks are now unblockable.

## Step 5: Handoff

Complete your role's **Success Checklist**, then use a handoff button:

- **Back to MainAgent** — default after completing a task
- **Continue <Role> Work** — claim the next ready task of your type
- **Request Testing** / **Report to Backend/Frontend** — when another teammate must act next

---

## Status Values

`ready` → `claimed` → `in-progress` → `review` / `completed`

Also: `blocked` (waiting on dependencies) and `failed` (attempted, errored).
