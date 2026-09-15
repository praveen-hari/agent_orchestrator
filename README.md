# Agent Orchestrator

A Software Development Lifecycle (SDLC) agent team for Code Studio. Specialist agents take a request from requirements through design, implementation, testing, and delivery.

Each feature lives in its own project folder so requirements, design, tasks, and results stay isolated.

## Cleaverview

The team follows a 3-phase workflow:

1. **Requirements** — `@RequirementsAnalyst` gathers specs and user stories
2. **Design** — `@SpecificationWriter` produces architecture and technical design; `@UniversalUIPlanner` can add UI plans
3. **Implementation** — `@MainAgent` decomposes work; `@BackendTeammate`, `@FrontendTeammate`, and `@TestingTeammate` execute it

## Agents

| Agent | Phase | Role |
| --- | --- | --- |
| **RequirementsAnalyst** | 1 | Functional specs, user stories, acceptance criteria |
| **SpecificationWriter** | 2 | Architecture, technical spec, API contracts, database schema |
| **UniversalUIPlanner** | 2 | Syncfusion UI/UX plans from existing theme tokens |
| **MainAgent** | 3 | Task decomposition, sprint tracking, teammate coordination |
| **BackendTeammate** | 3 | APIs, databases, server-side logic |
| **FrontendTeammate** | 3 | UI components, styling, client-side logic |
| **TestingTeammate** | 3 | Tests, quality checks, bug reports |

Agent definitions live in `.codestudio/agents/`.

## Quick start

### Full SDLC (recommended)

1. Start with `@RequirementsAnalyst` and describe the feature.
2. Answer clarifying questions (users, scope, constraints, success metrics).
3. Review `projects/{project-name}/requirements/requirements.md` and `user-stories.md`.
4. Type **approved**, then hand off to `@SpecificationWriter`.
5. Review architecture, technical spec, API spec, and database schema.
6. Optionally hand off to `@UniversalUIPlanner` for Syncfusion UI design.
7. Hand off to `@MainAgent` to create the sprint.
8. Hand off to `@BackendTeammate` or `@FrontendTeammate` to execute ready tasks.
9. Return to `@MainAgent` to unblock dependents and review progress.
10. Hand off to `@TestingTeammate` when implementation is ready to verify.

### Skip design (well-understood work)

```
@RequirementsAnalyst → @MainAgent → teammates
```

### Quick prototype (experimental only)

```
@MainAgent "Quick prototype: [describe feature]"
```

## Project folders

Every requirement gets its own folder. Use lowercase, hyphenated names (`auth-service`, `google-keep-todo`).

```bash
mkdir -p projects/{project-name}/{requirements,design,tasks,results}
```

That creates:

```
projects/{project-name}/
├── requirements/
│   ├── requirements.md
│   └── user-stories.md
├── design/
│   ├── architecture.md
│   ├── technical-spec.md
│   ├── api-spec.md
│   ├── database-schema.md
│   └── ui-design.md            # from UniversalUIPlanner
├── tasks/
│   ├── current-sprint.yaml     # lightweight index
│   ├── task-details/
│   │   ├── task-001.md
│   │   └── task-002.md
│   └── agent-log.md
└── results/
    └── task-{ID}-result.md
```

Do not mix files from different projects. Root `tasks/` holds **templates and examples only**.

## Repository layout

```
agent_orchestrator/
├── .codestudio/agents/              # Agent role definitions
│   ├── RequirementsAnalyst.agent.md
│   ├── SpecificationWriter.agent.md
│   ├── UIPlanner.agent.md
│   ├── MainAgent.agent.md
│   ├── BackendTeammate.agent.md
│   ├── FrontendTeammate.agent.md
│   └── TestingTeammate.agent.md
│
├── tasks/                           # Templates + example sprint
│   ├── requirements-template.md
│   ├── user-stories-template.md
│   ├── task-template.md
│   ├── agent-log-template.md
│   ├── current-sprint.yaml          # Example sprint index
│   └── task-details/                # Example task files
│
└── README.md
```

## Task tracking (YAML + Markdown)

Sprints use a hybrid format:

- `current-sprint.yaml` — fast index (epics, milestones, task status)
- `task-details/task-{ID}.md` — full context (acceptance criteria, files, work log)

**Why:** YAML stays small for status scans; Markdown holds the detail teammates need to execute.

### Task status

`ready` → `claimed` → `in-progress` → `review` → `completed`

Also: `blocked` (waiting on dependencies), `failed` (needs retry).

### Epic status

`planned` | `in-progress` | `completed` | `blocked`

Prefer tasks of 15–45 minutes. Split anything over 60 minutes into subtasks and checkpoints.

## Handoff flow

```
@RequirementsAnalyst
      ↓  [Requirements Complete → Design Architecture]
@SpecificationWriter
      ↓  [Design Complete → Start Implementation Planning]
      ↓  (optional) @UniversalUIPlanner → @FrontendTeammate
@MainAgent
      ↓  [Start Backend Work] or [Start Frontend Work]
@BackendTeammate / @FrontendTeammate
      ↓  [Back to Main Agent] or [Continue Work]
@MainAgent
      ↓  [Start Testing Work]
@TestingTeammate
      ↓  [Back to Main Agent] or [Report Bugs]
@MainAgent (final review)
```

## Templates

Copy these into a project folder as needed:

| Template | Destination |
| --- | --- |
| `tasks/requirements-template.md` | `projects/{name}/requirements/requirements.md` |
| `tasks/user-stories-template.md` | `projects/{name}/requirements/user-stories.md` |
| `tasks/current-sprint.yaml` | `projects/{name}/tasks/current-sprint.yaml` |
| `tasks/task-template.md` | `projects/{name}/tasks/task-details/task-{ID}.md` |
| `tasks/agent-log-template.md` | `projects/{name}/tasks/agent-log.md` |

## Guidelines

**RequirementsAnalyst**

- Create the project folder before writing docs
- Save both requirements files before asking for approval
- Do not hand off until the user explicitly approves

**SpecificationWriter**

- Design from the project requirements, not from memory
- Document trade-offs, not only the chosen approach
- Cover architecture, APIs, data, and implementation standards

**MainAgent**

- Never execute implementation tasks; delegate via handoffs
- Keep sprint YAML and task markdown in the project folder
- Unblock dependents when a task completes

**Teammates**

- Claim only `ready` tasks of your type
- Update status at every step
- Write a result file under `projects/{project-name}/results/`
- Log activity in `agent-log.md`

## Troubleshooting

**Agents missing from the picker**

- Confirm files are in `.codestudio/agents/`
- Confirm the extension is `.agent.md`
- Reload the Code Studio window

**Handoff does nothing**

- Target agent name must match the `name:` field in the agent file
- Check YAML frontmatter `handoffs` syntax

**Task claimed twice**

- Read status from `current-sprint.yaml` before claiming
- Update status immediately after claiming

## Success checks

- Specs are specific enough to design from
- Design is specific enough to implement without guessing
- Tasks complete on first try against acceptance criteria
- Bugs found in testing are reported back to the owning teammate
- Project folders stay isolated from each other
