# Standard Teammate Workflow Protocol

This document defines the standard workflow that all implementation teammates (Backend, Frontend, Testing, DevOps, etc.) follow when executing tasks.

---

## 🔄 5-Step Workflow

### Step 1: Claim a Task

1. Read `tasks/current-sprint.yaml` (lightweight index)
2. Filter tasks matching your specialization:
   - `type` matches your role (backend/frontend/testing/etc.)
   - `status === "ready"`
   - All `dependencies` are completed
3. Select highest priority: sort by `priority` (critical > high > medium > low), then `priority_score`
4. For long-running tasks: check if `is_long_running === true` and claim only if ready for extended work
5. Update task status in YAML:
   ```yaml
   status: claimed
   assigned_to: BackendTeammate
   claimed_at: 2026-02-19T10:00:00Z
   ```
6. Read full task details from `tasks/task-details/task-{ID}.md`
7. Log to `tasks/agent-log.md`:
   ```markdown
   ## [Timestamp] - [AgentName]
   - Claimed task-XXX: [Title]
   - Status: ready → claimed
   ```

### Step 2: Execute Task

1. Update task status in `current-sprint.yaml`: `status: in-progress`
2. Open task detail file: `tasks/task-details/task-{ID}.md`
3. Read full task context from markdown:
   - Overview section: description, dependencies
   - Files section: what to create/modify
   - Acceptance criteria checklist
   - Technical notes with standards references
   - Subtasks (if long-running task)
   - Checkpoints for progress tracking
4. Read epic context from `current-sprint.yaml`:
   - Related specs listed in `technical_context`
   - Other tasks in same epic for context
5. Read relevant specifications:
   - `tasks/technical-spec.md` - Implementation standards
   - `tasks/api-spec.md` - API contracts (if applicable)
   - `tasks/architecture.md` - System design
6. Implement the solution:
   - For tasks with subtasks: complete each, check off in markdown
   - Create files listed in Files section
   - Modify files as specified
   - Mark checkpoints complete with timestamps in markdown
   - Log work sessions in the task markdown Work Log section
   - Update progress percentage in markdown
   - Follow coding standards from specs
   - Add proper error handling
   - Include documentation/comments

### Step 3: Document Results

Create `tasks/task-results/task-{id}-result.md`:

```markdown
# Task {ID} Result: {Title}

**Completed by:** {AgentName}  
**Completed at:** {ISO timestamp}  
**Duration:** {minutes} minutes

## What Was Done
[Detailed description of implementation]

## Files Changed
- ✅ Created: `path/to/file1.ts`
- ✅ Modified: `path/to/file2.ts`

## Acceptance Criteria
- ✅ Criterion 1 - explanation of how it was met
- ✅ Criterion 2 - explanation of how it was met
- ✅ Criterion 3 - explanation of how it was met

## Technical Notes
[Any important implementation decisions, trade-offs, or considerations]

## Next Steps
[What tasks are now unblocked, recommendations for next work]

## Code Summary
\`\`\`[language]
// Key code snippet or interface
\`\`\`
```

### Step 4: Update Task Status

**In `tasks/current-sprint.yaml`**, update the completed task:

```yaml
tasks:
  - id: task-XXX
    status: completed
    assigned_to: BackendTeammate
    actual_duration: 20min
```

**In `tasks/task-details/task-XXX.md`**, update:
- Mark all checkboxes complete ✅
- Add completion timestamp to Timeline section
- Update Progress to 100%
- Add final work log entry

**Also update in `current-sprint.yaml`:**
- Epic progress: increment `completed_tasks`, recalculate `progress`
- Sprint metadata: increment `completed_count`, decrement `in_progress_count`
- Velocity factor: calculate from actual vs estimated times

### Step 5: Choose Next Action

Show handoff buttons for user to decide:

- **⬅️ Back to Main Agent** - Report completion, let team lead coordinate next steps
- **🔄 Continue [Your Type] Work** - Immediately claim next available task of your type
- **➡️ Hand to [Other Agent]** - If specific next step requires different expertise

Log completion to `tasks/agent-log.md`:
```markdown
## [Timestamp] - [AgentName]
- Completed task-XXX: [Title]
- Status: in-progress → completed
- Duration: [X] minutes
- Result: tasks/task-results/task-XXX-result.md
- Next: [What's unblocked or recommended]
```

---

## ⚠️ Important Rules

1. **Always update task status** when claiming, starting, completing
2. **Create result file** for every completed task
3. **Log to agent-log.md** for all significant actions
4. **Check dependencies** - never start a blocked task
5. **Be autonomous** - don't ask Main Agent for permission, just execute
6. **Update metadata** - Keep sprint counts accurate
7. **Test your work** - Verify it meets acceptance criteria before marking complete

---

## 📊 Task Status Values

| Status | Meaning | When to Use |
|--------|---------|-------------|
| `ready` | Can be claimed and worked on | Dependencies met, no blockers |
| `blocked` | Waiting for dependencies | Another task must complete first |
| `claimed` | Assigned to an agent | You've taken ownership |
| `in-progress` | Actively working | Implementation underway |
| `review` | Needs review before completion | Testing found issues, needs fixes |
| `completed` | Done and verified | All acceptance criteria met |
| `failed` | Attempted but encountered errors | Couldn't complete, needs escalation |

---

## 💡 Best Practices

### Code Quality
- Write clean, maintainable code following project standards
- Add meaningful comments for complex logic
- Handle errors gracefully with user-friendly messages
- Consider edge cases and error scenarios

### Documentation
- Be specific in result documents
- Include code snippets for key changes
- Document any deviations from original plan
- Explain non-obvious decisions

### Collaboration
- Update status promptly so others aren't blocked
- Document what you learned for future teammates
- Note any issues for Main Agent to address
- Suggest optimizations or improvements

### Efficiency
- Read all relevant specs before starting
- Don't ask for clarification if specs are clear
- Work autonomously within your expertise
- Batch similar tasks when possible

---

## 🎯 Success Criteria

Before marking a task `completed`, verify:

- [ ] All acceptance criteria met and documented
- [ ] Code follows technical-spec.md standards
- [ ] Files created/modified as specified
- [ ] Error handling implemented
- [ ] Testing performed (basic verification)
- [ ] Result document created in task-results/
- [ ] Task status updated in current-sprint.json
- [ ] Activity logged in agent-log.md
- [ ] Dependent tasks unblocked (if applicable)

---

**This workflow applies to:** BackendTeammate, FrontendTeammate, TestingTeammate, DevOpsTeammate, DocumentationTeammate, and any future implementation specialists.

**Reference this document** instead of repeating workflow steps in individual agent prompts.
