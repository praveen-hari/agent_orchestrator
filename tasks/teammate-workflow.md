# Standard Teammate Workflow Protocol

This document defines the standard workflow that all implementation teammates (Backend, Frontend, Testing, DevOps, etc.) follow when executing tasks.

---

## 🔄 5-Step Workflow

### Step 1: Claim a Task

1. Read `tasks/current-sprint.json`
2. Filter tasks matching your specialization:
   - `type` matches your role (backend/frontend/testing/etc.)
   - `status === "ready"`
   - All `dependencies` are completed
3. Select the highest priority task
4. Update task status:
   ```json
   {
     "status": "claimed",
     "assigned_to": "[YourAgentName]",
     "claimed_at": "[ISO timestamp]"
   }
   ```
5. Log to `tasks/agent-log.md`:
   ```markdown
   ## [Timestamp] - [AgentName]
   - Claimed task-XXX: [Title]
   - Status: ready → claimed
   ```

### Step 2: Execute Task

1. Update task status to `in-progress`
2. Read task requirements:
   - Task `description`
   - `acceptance_criteria`
   - `technical_notes`
3. Read relevant specifications:
   - `tasks/technical-spec.md` - Implementation standards
   - `tasks/api-spec.md` - API contracts (if applicable)
   - `tasks/architecture.md` - System design
4. Implement the solution:
   - Create files listed in `files_to_create`
   - Modify files listed in `files_to_modify`
   - Follow coding standards from technical-spec.md
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

In `tasks/current-sprint.json`, update the completed task:

```json
{
  "id": "task-XXX",
  "status": "completed",
  "assigned_to": "[YourAgentName]",
  "completed_at": "[ISO timestamp]",
  "result_file": "tasks/task-results/task-XXX-result.md"
}
```

Also update sprint metadata counts:
- Increment `metadata.completed_count`
- Decrement `metadata.in_progress_count`

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
