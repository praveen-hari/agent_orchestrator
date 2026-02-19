# Task-002: Implement Auth API Endpoints

**Status:** 🔴 Blocked | **Priority:** High | **Type:** Backend  
**Epic:** [epic-001 - Authentication System](../current-sprint.yaml#epic-001)  
**Assigned:** Not claimed | **Est:** 90min | **Actual:** —

---

## 📋 Overview

**Description:**  
Implement REST API endpoints for user authentication: register, login, logout, and token refresh. Includes input validation, password hashing, JWT generation, and comprehensive error handling.

**Dependencies:**  
- ⏳ task-001 - Database schema must exist first

---

## 📁 Files

### To Create
- `src/controllers/auth.controller.ts` - Auth business logic
- `src/routes/auth.routes.ts` - Express routes
- `src/services/auth.service.ts` - Auth service layer
- `src/validators/auth.validator.ts` - Input validation schemas
- `tests/integration/auth.test.ts` - Integration tests

### To Modify
- `src/routes/index.ts` - Register auth routes
- `src/app.ts` - Add error handling middleware

---

## ✅ Acceptance Criteria

- [ ] **POST /api/auth/register** - Creates user, returns JWT token
- [ ] **POST /api/auth/login** - Validates credentials, returns JWT
- [ ] **POST /api/auth/logout** - Invalidates token (optional: token blacklist)
- [ ] **POST /api/auth/refresh** - Issues new token from refresh token
- [ ] **Input validation** - All inputs validated with clear error messages
- [ ] **Password security** - Passwords hashed with bcrypt (10+ rounds)
- [ ] **Error handling** - Returns proper HTTP status codes (400, 401, 409, 500)
- [ ] **Tests pass** - All integration tests passing with >80% coverage

---

## 🔧 Technical Notes

**Standards & Specs:**
- Follow `tasks/api-spec.md` for exact endpoint contracts
- Follow `tasks/technical-spec.md` for error response format

**Implementation Details:**
- Use express-validator or Joi for input validation
- JWT secret from environment variable (never hardcode)
- Token expiry: access token 15min, refresh token 7 days
- Rate limiting: 5 attempts per 15min window per IP
- CORS: Allow credentials, specific origins only

**Error Messages:**
- 400: Invalid input (email format, password too short)
- 401: Invalid credentials
- 409: User already exists (email/username taken)
- 500: Server error (log details, show generic message)

**Considerations:**
- Security: Never return password hashes in responses
- Performance: Use database indexes for email lookups
- Edge cases: Handle SQL injection, timing attacks

---

## 📊 Progress Tracking

### Timeline
- **Claimed:** Not yet
- **Started:** Not yet  
- **Completed:** Not yet
- **Duration:** — (est: 90min)

### Current Progress: 0%

---

## 🎯 Subtasks

> Breaking this into 4 manageable pieces

- [ ] **Subtask 2.1:** Create validator schemas (15min)
  - Email, password, username validation rules
  
- [ ] **Subtask 2.2:** Implement register endpoint (25min)
  - Hash password, create user, generate JWT
  
- [ ] **Subtask 2.3:** Implement login endpoint (20min)
  - Verify credentials, compare hashed password, return JWT
  
- [ ] **Subtask 2.4:** Implement logout & refresh (15min)
  - Token invalidation logic, refresh token rotation
  
- [ ] **Subtask 2.5:** Add error handling & validation (10min)
  - Middleware, try-catch blocks, status codes
  
- [ ] **Subtask 2.6:** Write integration tests (15min)
  - Test all endpoints, edge cases, error scenarios

---

## 📍 Checkpoints

- [ ] **Checkpoint 1:** File structure created, dependencies installed _(timestamp)_
- [ ] **Checkpoint 2:** Register endpoint working
- [ ] **Checkpoint 3:** Login endpoint working
- [ ] **Checkpoint 4:** All endpoints tested and passing

---

## 📝 Work Log

_No work sessions yet. Claim this task to begin._

---

## 🧪 Testing Notes

**How to test:**
1. Start server: `npm run dev`
2. Register user: `POST /api/auth/register` with valid data
3. Login: `POST /api/auth/login` with credentials
4. Verify JWT: Decode token, check claims
5. Test errors: Invalid email, short password, duplicate user
6. Run automated tests: `npm test -- auth.test.ts`

**Expected results:**
- Register creates user and returns token
- Login with correct credentials succeeds
- Login with wrong password fails (401)
- Duplicate registration fails (409)
- All validation errors return 400 with clear messages

---

## 📦 Result

**Result File:** `tasks/task-results/task-002-result.md`  
**Status:** ⏳ Not completed yet

---

## 🐛 Issues & Notes

**Blockers:**
- Waiting for task-001 (database schema)

**Questions:**
- Should we implement refresh token rotation?
- Token blacklist for logout or just client-side removal?

**Security Considerations:**
- Rate limiting to prevent brute force
- Email verification before account activation?
- Password strength requirements (min 8 chars, mix of types)

**Related Tasks:**
- task-001 - Database schema (dependency)
- task-003 - JWT middleware (uses tokens from here)
- task-004 - Login UI (consumes these endpoints)

---

## 🏷️ Metadata

```yaml
id: task-002
epic_id: epic-001
created_at: 2026-02-19T10:00:00Z
updated_at: 2026-02-19T10:00:00Z
retry_count: 0
error: null
is_long_running: true
has_subtasks: true
```

**Tags:** #backend #api #authentication #jwt #security #high-priority
