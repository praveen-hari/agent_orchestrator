# 🤖 VS Code Agent Team - SDLC Orchestration System

A complete Software Development Lifecycle (SDLC) agent team using VS Code's native custom agents with handoffs. This system takes you from requirements gathering through design, implementation, testing, and delivery.

## 📋 Overview

This agent team follows a structured 3-phase SDLC workflow:

1. **Phase 1: Requirements** → `@RequirementsAnalyst` gathers requirements and creates specifications
2. **Phase 2: Design** → `@SpecificationWriter` creates technical architecture and design docs
3. **Phase 3: Implementation** → `@MainAgent` orchestrates, `@Teammates` execute

## 🎯 Available Agents

### Phase 1: Requirements Gathering
- **@RequirementsAnalyst** - Gathers requirements, creates functional specs and user stories

### Phase 2: Technical Design
- **@SpecificationWriter** - Creates architecture, technical specs, API design, database schema

### Phase 3: Implementation & Coordination
- **@MainAgent** - Team orchestrator, decomposes design into tasks, coordinates teammates
- **@BackendTeammate** - Implements APIs, databases, server-side logic
- **@FrontendTeammate** - Implements UI components, styling, client-side logic
- **@TestingTeammate** - Runs tests, verifies quality, documents bugs

## 🚀 Quick Start

### Option A: Full SDLC (Recommended for Production)

```
1. Start with requirements:
   You: @RequirementsAnalyst "Build a todo app with React and Node"
   
2. Answer clarifying questions about users, features, constraints

3. Review requirements.md and user-stories.md

4. Click handoff → @SpecificationWriter

5. Review architecture.md, technical-spec.md, api-spec.md, database-schema.md

6. Click handoff → @MainAgent

7. Review current-sprint.json task breakdown

8. Click handoff → @BackendTeammate or @FrontendTeammate

9. Agents execute tasks, update status, create results

10. Click handoff → @MainAgent to review progress

11. Repeat until all tasks complete
```

### Option B: Skip Design (Well-Understood Requirements)

```
1. @RequirementsAnalyst "Build feature X"
2. Review requirements
3. Handoff → @MainAgent (skip SpecificationWriter)
4. @MainAgent creates tasks
5. @Teammates execute
```

### Option C: Quick Prototype (Experimental Only)

```
1. @MainAgent "Quick prototype: [describe feature]"
2. @MainAgent creates simple task list
3. @Teammates execute
```

## 📁 File Structure

```
agent_orchestrator/
├── .codestudio/
│   └── agents/                          # VS Code custom agents
│       ├── RequirementsAnalyst.agent.md
│       ├── SpecificationWriter.agent.md
│       ├── MainAgent.agent.md
│       ├── BackendTeammate.agent.md
│       ├── FrontendTeammate.agent.md
│       └── TestingTeammate.agent.md
│
├── tasks/
│   ├── requirements.md                  # Phase 1 output
│   ├── user-stories.md                  # Phase 1 output
│   ├── architecture.md                  # Phase 2 output
│   ├── technical-spec.md                # Phase 2 output
│   ├── api-spec.md                      # Phase 2 output
│   ├── database-schema.md               # Phase 2 output
│   │
│   ├── current-sprint.yaml              # 🆕 Lightweight task index (YAML)
│   ├── task-details/                    # 🆕 Detailed task context (Markdown)
│   │   ├── task-001.md
│   │   ├── task-002.md
│   │   └── task-XXX.md
│   │
│   ├── task-results/                    # Completed task outputs
│   ├── agent-log.md                     # Activity timeline
│   └── HYBRID-FORMAT-GUIDE.md           # 🆕 Format documentation
│
└── README.md                            # This file
```

**🎯 New Hybrid Format:** Sprint tracking now uses YAML index + Markdown task files for 80% less token usage and better LLM efficiency!

## 📋 Workflow Example

### Complete Flow: "Build a Todo App"

**Phase 1: Requirements (15-20 minutes)**

```
You → @RequirementsAnalyst "Build a todo app with React frontend and Node.js backend"

RequirementsAnalyst asks:
- Who will use this? (personal use or team collaboration?)
- What features are essential? (CRUD only, or tags, search, filters?)
- Performance requirements? (expected users, data volume)
- Security needs? (authentication required?)

You answer questions

RequirementsAnalyst creates:
✅ tasks/requirements.md
   - 10 functional requirements (FR-1 to FR-10)
   - 5 non-functional requirements (performance, security, etc.)
   - Technical constraints (React, Node, PostgreSQL)
   
✅ tasks/user-stories.md
   - 15 user stories with acceptance criteria
   - Story points for estimation

Click [✅ Requirements Complete → Design Architecture]
```

**Phase 2: Design (30-45 minutes)**

```
You → @SpecificationWriter (via handoff)

SpecificationWriter reads requirements and creates:
✅ tasks/architecture.md
   - System architecture diagram
   - 3-tier design (React → Express API → PostgreSQL)
   - Technology stack justifications
   - Security architecture
   - Performance strategy
   
✅ tasks/technical-spec.md
   - Code standards (TypeScript, ESLint rules)
   - Error handling patterns
   - Module specifications with interfaces
   
✅ tasks/api-spec.md
   - 8 REST endpoints with request/response schemas
   - Authentication flow (JWT)
   
✅ tasks/database-schema.md
   - users table (id, email, password_hash)
   - tasks table (id, user_id, title, completed, etc.)
   - Indexes for performance

Click [✅ Design Complete → Start Implementation Planning]
```

**Phase 3: Implementation (2-3 hours)**

```
You → @MainAgent (via handoff)

MainAgent reads all design docs and creates:
✅ tasks/current-sprint.json
   - 25 tasks broken down from design
   - Dependencies mapped (task B depends on task A)
   - Priorities assigned (critical path first)

Example tasks:
1. Create database schema (backend, 15min, ready)
2. Implement auth endpoints (backend, 30min, blocked by #1)
3. Create React components (frontend, 45min, ready)
4. Integrate API calls (frontend, 30min, blocked by #2, #3)
5. Test authentication (testing, 20min, blocked by #4)

Click [🔧 Start Backend Work]
```

```
You → @BackendTeammate (via handoff)

BackendTeammate:
1. Claims task-001 (database schema)
2. Updates status: ready → claimed → in-progress
3. Creates src/models/todo.model.ts
4. Updates status: in-progress → completed
5. Creates tasks/task-results/task-001-result.md
6. Logs activity to tasks/agent-log.md

Shows handoffs:
[⬅️ Back to Main Agent]
[🔧 Continue Backend Work]
[✅ Request Testing]

Click [🔧 Continue Backend Work]
```

```
BackendTeammate continues:
- Claims task-002 (auth endpoints)
- Implements login/register API
- Creates task result
- Completes task

Click [⬅️ Back to Main Agent]
```

```
You → @MainAgent (via handoff)

MainAgent:
- Reads current-sprint.json
- Sees tasks-001, 002 completed
- Unblocks task-004 (integration) - changes status blocked → ready
- Shows progress summary:
  ✅ Completed: 2 tasks (8%)
  🔄 In Progress: 0 tasks
  ⏳ Ready: 5 tasks (20%)
  🚫 Blocked: 18 tasks (72%)

Suggests: "Frontend work can start now. Backend should continue with task-003."

Click [🎨 Start Frontend Work]
```

```
You → @FrontendTeammate (via handoff)

FrontendTeammate:
- Claims task-010 (create TodoList component)
- Implements React component
- Makes it responsive
- Ensures accessibility
- Creates result with screenshots
- Completes task

Click [⬅️ Back to Main Agent]
```

**This pattern continues until all 25 tasks complete.**

## 🔄 Handoff Flow

```
@RequirementsAnalyst
      ↓ [✅ Requirements Complete → Design Architecture]
@SpecificationWriter
      ↓ [✅ Design Complete → Start Implementation Planning]
@MainAgent
      ↓ [🔧 Start Backend Work] or [🎨 Start Frontend Work]
@BackendTeammate / @FrontendTeammate
      ↓ [⬅️ Back to Main Agent] or [🔧 Continue Work]
@MainAgent
      ↓ [✅ Start Testing Work]
@TestingTeammate
      ↓ [⬅️ Back to Main Agent] or [🐛 Report Bugs]
@MainAgent (Final Review & Delivery)
```

## 📊 Task Status Flow

```
ready → claimed → in-progress → completed
                            ↓
                          review (if bugs found)
                            ↓
                          failed (if can't fix)
```

## ⚠️ Important Guidelines

### For RequirementsAnalyst
- ✅ Ask clarifying questions before documenting
- ✅ Cover functional AND non-functional requirements
- ✅ Document assumptions and risks
- ❌ Don't skip to implementation without validation

### For SpecificationWriter
- ✅ Design within technical constraints
- ✅ Document trade-offs and alternatives
- ✅ Create detailed specs developers can follow
- ❌ Don't over-engineer or under-engineer

### For MainAgent
- ✅ Decompose design into granular tasks (15-45 min each)
- ✅ Map dependencies accurately
- ✅ Unblock tasks when dependencies complete
- ❌ Don't execute tasks yourself - delegate!

### For Teammates (Backend, Frontend, Testing)
- ✅ Update task status at each step
- ✅ Create detailed result documents
- ✅ Log all activities
- ❌ Don't start blocked tasks
- ❌ Don't skip acceptance criteria

## 🎓 Tips & Best Practices

### When to Use Full SDLC (Phase 1 → 2 → 3)
- Production features
- Complex systems
- Team projects
- When requirements unclear

### When to Skip Phases
- Well-understood requirements (skip Phase 1)
- Simple CRUD apps (skip Phase 2)
- Quick experiments (start at Phase 3)
- Bug fixes (start at Phase 3)

### How to Handle Bugs
```
@TestingTeammate finds bugs
      ↓ [🐛 Report to Backend/Frontend]
@BackendTeammate fixes bugs
      ↓ [✅ Request Testing]
@TestingTeammate re-tests
      ↓ [⬅️ Back to Main Agent]
@MainAgent continues workflow
```

### How to Add New Specialists
1. Create new `.agent.md` file in `.github/agents/`
2. Define tools, handoffs, instructions
3. Add handoffs from MainAgent to new specialist
4. Add handoffs back to MainAgent

## 📚 Templates Available

- `tasks/requirements-template.md` - For RequirementsAnalyst
- `tasks/user-stories-template.md` - For RequirementsAnalyst
- `tasks/current-sprint.yaml` - 🆕 YAML sprint index (MainAgent)
- `tasks/task-template.md` - 🆕 Markdown task detail template
- `tasks/current-sprint-template.json` - Legacy JSON format (still supported)

**Recommended:** Use the new hybrid YAML + Markdown format for 80% better token efficiency!

## 🐛 Troubleshooting

### Agents don't appear in dropdown
- Ensure files are in `.github/agents/` directory
- Check file extension is `.agent.md`
- Reload VS Code window

### Handoff button doesn't work
- Verify target agent name matches filename (without .agent.md)
- Check handoff syntax in YAML frontmatter
- Ensure prompt is properly formatted

### Task claimed twice
- Check task status before claiming
- Update status atomically (read → check → update together)
- Add timestamps to detect race conditions

## 📈 Success Metrics

Track these to measure team effectiveness:

- **Requirements Quality:** Are specs clear enough to design from?
- **Design Quality:** Can developers implement without guessing?
- **Task Completion Rate:** What % of tasks complete on first try?
- **Bug Rate:** How many bugs found in testing?
- **Velocity:** How many story points completed per sprint?

## 🎯 Next Steps

1. **Try it out:** Start with `@RequirementsAnalyst` and a simple feature
2. **Follow the flow:** Go through all 3 phases to see the complete workflow
3. **Customize:** Modify agents to match your team's processes
4. **Add specialists:** Create DevOpsTeammate, DocumentationTeammate as needed
5. **Share feedback:** Improve the system based on real usage

## 📖 Additional Resources

- VS Code Custom Agents Documentation: https://code.visualstudio.com/docs/copilot/copilot-custom-agents
- Handoffs Guide: https://code.visualstudio.com/docs/copilot/copilot-custom-agents#handoffs
- Full Specification: `tasks/vscode-agent-team-specification.md`

---

**Built with ❤️ using VS Code Custom Agents**

Happy building! 🚀
