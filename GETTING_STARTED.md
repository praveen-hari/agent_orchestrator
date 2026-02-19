# 🚀 Getting Started with Agent Team

Welcome! This guide will walk you through your first complete SDLC workflow using the agent team.

## ✅ What You Just Installed

### Agent Files (`.github/agents/`)
- ✅ `RequirementsAnalyst.agent.md` - Phase 1: Requirements gathering
- ✅ `SpecificationWriter.agent.md` - Phase 2: Technical design  
- ✅ `MainAgent.agent.md` - Phase 3: Task orchestration
- ✅ `BackendTeammate.agent.md` - Backend implementation
- ✅ `FrontendTeammate.agent.md` - Frontend implementation
- ✅ `TestingTeammate.agent.md` - QA and testing

### Template Files (`tasks/`)
- ✅ `requirements-template.md` - For documenting requirements
- ✅ `user-stories-template.md` - For user stories
- ✅ `current-sprint-template.json` - For task lists
- ✅ `agent-log-template.md` - For activity tracking

### Documentation
- ✅ `README.md` - Complete system overview
- ✅ `vscode-agent-team-specification.md` - Full technical specification
- ✅ `GETTING_STARTED.md` - This file!

## 🎯 Your First Workflow: Build a Simple Feature

Let's build a simple feature to learn the system. We'll create a user registration system.

### Step 1: Start with Requirements (5 minutes)

Open VS Code chat and type:

```
@RequirementsAnalyst Create a user registration system with email and password. 
Users should be able to register, receive a confirmation email, and login.
```

**What will happen:**
- RequirementsAnalyst will ask clarifying questions:
  - What validation rules for passwords?
  - What happens if email already exists?
  - Any rate limiting needed?
  - What security standards to follow?

**Your job:** Answer the questions based on your needs.

**Output:** 
- `tasks/requirements.md` will be created with functional requirements
- `tasks/user-stories.md` will have user stories like:
  ```
  US-1: User Registration
  As a new user
  I want to create an account with email and password
  So that I can access the system
  
  Acceptance Criteria:
  ✅ Email must be unique
  ✅ Password must be 8+ chars with uppercase, lowercase, number
  ✅ Confirmation email sent after registration
  ```

**Next:** Click the handoff button that appears:  
`[✅ Requirements Complete → Design Architecture]`

---

### Step 2: Create Technical Design (10 minutes)

**What will happen:**
- SpecificationWriter reads your requirements
- Creates technical architecture design
- Specifies API endpoints
- Designs database schema

**Output:**
- `tasks/architecture.md` - System design
- `tasks/technical-spec.md` - Implementation standards
- `tasks/api-spec.md` - API contracts:
  ```
  POST /api/auth/register
  Request: { email: string, password: string }
  Response: { user: User, token: JWT }
  ```
- `tasks/database-schema.md` - users table definition

**Review these files** to ensure the design looks good!

**Next:** Click the handoff button:  
`[✅ Design Complete → Start Implementation Planning]`

---

### Step 3: Get Task Breakdown (2 minutes)

**What will happen:**
- MainAgent reads all design documents
- Breaks down into discrete tasks
- Maps dependencies
- Creates work plan

**Output:**
- `tasks/current-sprint.json` with tasks like:
  ```json
  {
    "id": "task-001",
    "title": "Create user database schema",
    "type": "backend",
    "status": "ready",
    "estimated_duration": "15min"
  },
  {
    "id": "task-002",
    "title": "Implement register endpoint",
    "type": "backend",
    "status": "blocked",
    "dependencies": ["task-001"]
  }
  ```

**Next:** Choose which work stream to start:
- `[🔧 Start Backend Work]` - Implement server-side
- `[🎨 Start Frontend Work]` - Implement UI
- `[📊 Review Progress]` - See status

Let's start with backend! Click `[🔧 Start Backend Work]`

---

### Step 4: Backend Implementation (20-30 minutes)

**What will happen:**
- BackendTeammate claims first backend task (task-001)
- Updates status: ready → claimed → in-progress
- Creates the database schema file
- Writes code following technical-spec.md
- Creates result document
- Updates status: in-progress → completed

**You can watch the progress:**
- Check `tasks/current-sprint.json` for status updates
- Check `tasks/agent-log.md` for activity timeline
- Check `tasks/task-results/` for completed work

**Next actions:**
- Click `[🔧 Continue Backend Work]` to do next task
- Click `[⬅️ Back to Main Agent]` to review progress

**Let BackendTeammate continue** until all backend tasks complete!

---

### Step 5: Progress Review (2 minutes)

Click `[⬅️ Back to Main Agent]`

**What will happen:**
- MainAgent reads current-sprint.json
- Checks which tasks are completed
- Unblocks dependent tasks
- Shows progress report:
  ```
  ✅ Completed: 5 tasks (42%)
  🔄 In Progress: 0 tasks
  ⏳ Ready: 3 tasks (25%)
  🚫 Blocked: 4 tasks (33%)
  ```

**Next:** Click `[🎨 Start Frontend Work]` to implement UI

---

### Step 6: Frontend Implementation (30-45 minutes)

**What will happen:**
- FrontendTeammate claims frontend tasks
- Creates React components
- Implements forms with validation
- Integrates with backend API
- Ensures responsive design
- Makes it accessible

**Files created:**
- `src/components/RegisterForm.tsx`
- `src/components/LoginForm.tsx`
- `src/services/auth.service.ts`

---

### Step 7: Testing (15-20 minutes)

Click `[✅ Start Testing Work]`

**What will happen:**
- TestingTeammate runs integration tests
- Tests API endpoints
- Tests UI components
- Verifies acceptance criteria
- Documents any bugs found

**If bugs found:**
- TestingTeammate creates detailed bug report
- Click `[🐛 Report to Backend]` or `[🎨 Report to Frontend]`
- Teammate fixes bugs
- Re-test to verify fixes

---

### Step 8: Completion & Review

Click `[⬅️ Back to Main Agent]`

**What will happen:**
- MainAgent checks all tasks completed
- Aggregates all results
- Creates final summary
- Presents deliverables

**You now have:**
- ✅ Complete user registration system
- ✅ Documented requirements
- ✅ Technical design docs
- ✅ Clean, tested code
- ✅ All acceptance criteria met

---

## 🎓 What You Learned

1. **Phase 1: Requirements** - Always start with clear requirements
2. **Phase 2: Design** - Design before coding saves rework
3. **Phase 3: Implementation** - Break work into small tasks
4. **Handoffs** - Seamlessly transition between specialists
5. **Task Management** - Track status in current-sprint.json
6. **Documentation** - Every phase produces artifacts
7. **Quality** - Testing verifies acceptance criteria

---

## 🔥 Try These Next

### Beginner Projects
1. **Todo App** - Classic CRUD application
2. **Blog System** - Posts with comments
3. **Contact Form** - Simple form with validation

### Intermediate Projects
1. **E-commerce Store** - Products, cart, checkout
2. **Social Media Feed** - Posts, likes, comments
3. **Project Management Tool** - Tasks, sprints, teams

### Advanced Projects
1. **Real-time Chat** - WebSockets, authentication
2. **API Gateway** - Microservices architecture
3. **Admin Dashboard** - Data visualization, analytics

---

## 💡 Tips for Success

### Do's ✅
- Always start with RequirementsAnalyst for production features
- Read the design documents before coding
- Let agents complete tasks autonomously
- Review progress regularly with MainAgent
- Document bugs clearly for testing

### Don'ts ❌
- Don't skip requirements for complex features
- Don't manually code what agents can do
- Don't ignore failing tests
- Don't start blocked tasks
- Don't forget to update task status

---

## 🐛 Common Issues & Solutions

### Issue: Agent doesn't appear in dropdown
**Solution:** 
- Reload VS Code window (Cmd+R on Mac, Ctrl+R on Windows)
- Check file is in `.github/agents/` directory
- Verify file extension is `.agent.md`

### Issue: Handoff button doesn't work
**Solution:**
- The target agent might not exist yet (give it a moment)
- Check agent name in handoff matches filename
- Try typing `@AgentName` manually

### Issue: Task claimed twice
**Solution:**
- Check current-sprint.json before claiming
- Update status immediately after claiming
- Add timestamp to detect conflicts

### Issue: Design doesn't match requirements
**Solution:**
- Ask SpecificationWriter to revise design
- Use handoff `[⬅️ Need Requirements Clarification]`
- Iterate until design is correct

---

## 📚 Additional Resources

### Documentation
- [README.md](README.md) - Complete system overview
- [Full Specification](tasks/vscode-agent-team-specification.md) - Detailed technical spec
- [VS Code Agent Docs](https://code.visualstudio.com/docs/copilot/copilot-custom-agents)

### Templates
- Use templates in `tasks/` folder as starting points
- Customize templates for your team's needs
- Create new templates for recurring patterns

### Community
- Share your experience and feedback
- Suggest improvements to agents
- Create new specialist agents

---

## 🎉 You're Ready!

You now know how to:
- ✅ Use the complete SDLC agent team
- ✅ Navigate through phases with handoffs
- ✅ Track progress with task management
- ✅ Build production-quality features

**Start your first project now!** 

Open VS Code chat and type:
```
@RequirementsAnalyst [Describe your project]
```

Happy building! 🚀

---

**Questions or issues?** 
- Check README.md for detailed documentation
- Review agent files for specific behaviors
- Modify agents to fit your workflow
