# Quick Start Guide

[中文](QUICK_START.zh-CN.md) | English

Learn to use the Context Sync plugin in 5 minutes.

## Installation

```bash
# Method 1: Install from GitHub (Recommended)
/plugin marketplace add Claudate/claude-code-context-sync
/plugin install context-sync

# Method 2: Local development installation
git clone https://github.com/Claudate/claude-code-context-sync.git
/plugin marketplace add ./claude-code-context-sync
/plugin install context-sync
```

## Basic Usage

### Scenario 1: Save Current Work Progress

You're working on user authentication and suddenly need to switch to an urgent task:

```bash
# In current window
> I'm implementing JWT authentication, completed token generation, still need to add refresh mechanism
> /save-session

✅ Context saved to: docs/context-sessions/20251210-1430-jwt-auth.md

To resume in new window:
1. Use /resume-session
2. Select the corresponding session file

Pending tasks: 3
```

### Scenario 2: Resume Previous Work

Continue previous work in a new window or later:

```bash
> /resume-session

📋 Available Session List:

1. 20251210-1430-jwt-auth.md
   Pending tasks: 3

2. 20251210-1500-payment-bug.md
   Pending tasks: 1

Which session would you like to resume? (enter number or filename)

> 1

📂 Loaded Session: jwt-auth

# Session: JWT Authentication Implementation

## Pending Tasks
- [ ] 🔴 High Priority: Implement token refresh mechanism
- [ ] 🟡 Medium Priority: Add password encryption
- [ ] 🟢 Low Priority: Add OAuth integration

🎯 Which task to work on? Or shall I continue with the previous work?

> Continue implementing token refresh mechanism
```

## Common Commands

| Command | Description | Example |
|---------|-------------|---------|
| `/save-session` | Save current session | Save work progress anytime |
| `/resume-session` | Resume previous session | List and select session to resume |
| `换窗口处理-` | Auto-trigger save | Chinese shortcut command |

## Useful Tips

### 1. Task Priority Management

Use priority markers to quickly identify important tasks:

- 🔴 **High Priority**: Blocking tasks, core features
- 🟡 **Medium Priority**: Important but not urgent
- 🟢 **Low Priority**: Nice-to-have, optimizations

### 2. Working on Multiple Projects

Create separate sessions for each feature when developing multiple features:

```bash
# Project A - User Authentication
> /save-session
✅ Saved to: 20251210-1430-user-auth.md

# Project B - Payment Integration
> /save-session
✅ Saved to: 20251210-1500-payment-integration.md

# Project C - Performance Optimization
> /save-session
✅ Saved to: 20251210-1600-performance-opt.md
```

### 3. Work Handoff

Share session files with team members:

```bash
# Export session
cp docs/context-sessions/20251210-1430-feature-x.md /path/to/share/

# Colleague can import and continue
cp /path/to/shared/20251210-1430-feature-x.md docs/context-sessions/
> /resume-session
```

## Session File Example

```markdown
# Session: Implementing User Authentication

## Metadata
- **Created**: 2025-12-10 14:30
- **Status**: In Progress

## Context Summary
Implementing JWT-based user authentication system with login, registration, token refresh.

## Completed Tasks
- [x] Installed jsonwebtoken library
- [x] Created auth middleware
- [x] Implemented token generation logic

## Pending Tasks
- [ ] 🔴 High Priority: Implement token refresh endpoint
- [ ] 🔴 High Priority: Add password hashing
- [ ] 🟡 Medium Priority: Add login failure rate limiting
- [ ] 🟢 Low Priority: Integrate OAuth2

## Key Files
- `backend/auth/jwt.service.ts` - JWT service
- `backend/middleware/auth.middleware.ts` - Auth middleware
- `backend/routes/auth.routes.ts` - Auth routes

## Notes
- Token expiry set to 1 hour
- Refresh tokens stored in httpOnly cookies
- Passwords need bcrypt encryption

## Next Steps
1. Read jwt.service.ts to understand current implementation
2. Add /auth/refresh endpoint
3. Test token refresh flow
```

## Suggested Workflow

### Development Flow

```
1. Start new task
   ↓
2. Work for a while
   ↓
3. Need to switch tasks?
   ├─ Yes → /save-session → Switch to new task
   └─ No → Continue working
   ↓
4. Resume previous task
   ↓
5. /resume-session
   ↓
6. Select session and continue
   ↓
7. Session auto-deleted after all tasks complete
```

### Daily Work Habits

**Morning:**
```bash
> /resume-session
# Review yesterday's pending tasks
# Continue development
```

**During Work:**
```bash
# Save important progress anytime
> /save-session
```

**Before End of Day:**
```bash
> /save-session
# Ensure work progress is saved
# Can quickly resume next day
```

## FAQ

### Q: Where are session files saved?

A: Saved in your project's `docs/context-sessions/` directory.

### Q: How to delete a session?

A: Auto-deleted when all tasks complete, or manually delete the file:
```bash
rm docs/context-sessions/filename.md
```

### Q: Can I use it across different projects?

A: Yes! Each project has its own `docs/context-sessions/` directory.

### Q: Can I manually edit session files?

A: Yes! They are standard Markdown files and can be edited anytime.

## Next Steps

- Read the complete [README](README.md) to learn all features
- Check [DEPLOYMENT](DEPLOYMENT.md) to learn how to publish plugins
- Visit GitHub Issues to report problems or suggestions

---

**Start using now!** Save your first session with `/save-session` 🚀
