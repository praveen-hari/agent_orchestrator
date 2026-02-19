# Task-001: Create Database Schema

**Status:** 🟢 Ready | **Priority:** Critical | **Type:** Backend  
**Epic:** [epic-001 - Authentication System](../current-sprint.yaml#epic-001)  
**Assigned:** Not claimed | **Est:** 15min | **Actual:** —

---

## 📋 Overview

**Description:**  
Create the database schema for user authentication, including users table with proper fields, indexes, and constraints. This is the foundation for the entire authentication system.

**Dependencies:**  
- None (this is a foundational task)

---

## 📁 Files

### To Create
- `src/models/user.model.ts` - Mongoose/Sequelize user model
- `migrations/001-create-users-table.sql` - Database migration
- `migrations/001-rollback.sql` - Rollback script

### To Modify
- `src/models/index.ts` - Export new user model

---

## ✅ Acceptance Criteria

- [ ] **Users table created** with fields: id, email, username, password_hash, created_at, updated_at
- [ ] **Indexes added** on email (unique) and username (unique) for fast lookups
- [ ] **Constraints enforced:** email and username must be unique, not null
- [ ] **Migration tested:** Can run up/down migrations successfully
- [ ] **Model exports:** User model properly typed and exported

---

## 🔧 Technical Notes

**Standards & Specs:**
- Follow `tasks/database-schema.md` for field naming conventions
- Follow `tasks/technical-spec.md` for TypeScript typing standards

**Implementation Details:**
- Use bcrypt for password hashing (min 10 rounds)
- Email field: lowercase, trimmed, max 255 chars
- Username: alphanumeric + underscore, 3-30 chars
- Add timestamps (created_at, updated_at) automatically
- Use UUIDs for primary keys

**Considerations:**
- Performance: Index on email for login lookups
- Security: NEVER store plain passwords
- Scalability: Consider partitioning strategy for future

---

## 📊 Progress Tracking

### Timeline
- **Claimed:** Not yet
- **Started:** Not yet  
- **Completed:** Not yet
- **Duration:** — (est: 15min)

### Current Progress: 0%

---

## 🎯 Subtasks

> Simple task, no subtasks needed (estimated <30min)

---

## 📍 Checkpoints

- [ ] **Checkpoint 1:** Schema designed and reviewed
- [ ] **Checkpoint 2:** Migration script written
- [ ] **Checkpoint 3:** Model file created with types
- [ ] **Checkpoint 4:** Migration tested locally

---

## 📝 Work Log

_No work sessions yet. Claim this task to begin._

---

## 🧪 Testing Notes

**How to test:**
1. Run migration: `npm run migrate:up`
2. Verify table exists: `psql -d mydb -c "\d users"`
3. Test rollback: `npm run migrate:down`
4. Re-run migration to confirm idempotency

**Expected results:**
- Table created with all fields and constraints
- Indexes visible in database
- Model can be imported without errors

---

## 📦 Result

**Result File:** `tasks/task-results/task-001-result.md`  
**Status:** ⏳ Not completed yet

---

## 🐛 Issues & Notes

**Blockers:**
- None

**Questions:**
- None

**Related Tasks:**
- task-002 - Auth API (depends on this schema)
- task-003 - JWT middleware (uses this model)

---

## 🏷️ Metadata

```yaml
id: task-001
epic_id: epic-001
created_at: 2026-02-19T10:00:00Z
updated_at: 2026-02-19T10:00:00Z
retry_count: 0
error: null
```

**Tags:** #backend #database #schema #foundation #critical
