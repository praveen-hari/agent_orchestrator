# Sprint Index (`tasks/current-sprint.yaml`)

`tasks/current-sprint.yaml` is a lightweight, human-editable overview of the current sprint.

## What it tracks

- **Sprint metadata:** IDs, timestamps, user request summary
- **Epics:** groups of related tasks (progress, dependencies, context)
- **Tasks:** minimal per-task info (status, owner, estimate, links to detail files)
- **Work sessions:** a short log of who is active and what finished

## Typical workflow

1. Update statuses quickly in `tasks/current-sprint.yaml`.
2. Put deep context, checklists, and logs in `tasks/task-details/task-XXX.md`.
3. Keep task dependencies accurate so “blocked → ready” transitions are obvious.

## Status values

The index uses a small status vocabulary (examples you’ll see in this repo):

- `ready`, `blocked`, `claimed`, `in-progress`, `review`, `completed`, `failed`

## Notes on references

Some example entries reference spec files like `tasks/technical-spec.md` or `tasks/api-spec.md`. Those paths may be placeholders depending on how you structure your project—create them if you want the references to be real.
