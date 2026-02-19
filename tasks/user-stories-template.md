# User Stories: [Project Name]

**Created:** [Date]  
**Created By:** RequirementsAnalyst  
**Sprint:** [Sprint ID or Phase]

## Epic 1: [Epic Name]

### US-1: [User Story Title]
**As a** [user type]  
**I want to** [action/capability]  
**So that** [benefit/value]

**Acceptance Criteria:**
- ✅ Criterion 1 (specific, testable condition)
- ✅ Criterion 2 (specific, testable condition)
- ✅ Criterion 3 (specific, testable condition)

**Priority:** Must Have | Should Have | Nice to Have  
**Story Points:** [1-13, Fibonacci scale]  
**Dependencies:** [List user story IDs this depends on]  
**Notes:** [Any additional context or clarifications]

---

### US-2: [User Story Title]
**As a** [user type]  
**I want to** [action/capability]  
**So that** [benefit/value]

**Acceptance Criteria:**
- ✅ Criterion 1
- ✅ Criterion 2

**Priority:** Must Have | Should Have | Nice to Have  
**Story Points:** [1-13]  
**Dependencies:** US-1  
**Notes:**

---

## Epic 2: [Epic Name]

### US-3: [User Story Title]
**As a** [user type]  
**I want to** [action/capability]  
**So that** [benefit/value]

**Acceptance Criteria:**
- ✅ Criterion 1
- ✅ Criterion 2
- ✅ Criterion 3

**Priority:** Must Have | Should Have | Nice to Have  
**Story Points:** [1-13]  
**Dependencies:** US-1, US-2  
**Notes:**

---

[Add more user stories as needed]

---

## Summary

**Total Epics:** [X]  
**Total User Stories:** [Y]  
**Total Story Points:** [Z]

### By Priority
- **Must Have:** [X] stories, [Y] points
- **Should Have:** [X] stories, [Y] points
- **Nice to Have:** [X] stories, [Y] points

### Estimated Sprint Duration
Based on story points and team velocity: [Duration estimate]

---

## User Story Writing Tips

### Good User Story Example:
```
US-5: User Login
As a registered user
I want to log into my account with email and password
So that I can access my personal dashboard

Acceptance Criteria:
✅ User can enter email and password in login form
✅ System validates credentials against database
✅ Valid credentials redirect to dashboard with JWT token
✅ Invalid credentials show error message "Invalid email or password"
✅ Failed login attempts are rate-limited (max 5 per 15 minutes)
✅ Password is masked (••••) when typing
```

### Bad User Story Example (Too Vague):
```
❌ As a user I want to use the system

Problems:
- No specific action
- No clear benefit
- No acceptance criteria
- Can't estimate or test
```

---

**Status:** Draft | In Review | Approved  
**Next Steps:** Hand off to SpecificationWriter for technical design
