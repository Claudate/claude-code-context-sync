# Context Sync Plugin for Claude Code

English | [简体中文](README.zh-CN.md)

Save and resume Claude Code session context across multiple windows. Never lose track of your work progress when switching between different projects or tasks.

## Features

- **Smart Context Saving**: Automatically extracts and saves:
  - Completed and pending tasks
  - Key files being worked on
  - Technical decisions and notes
  - Priority-based task organization

- **Easy Session Recovery**: Resume previous work sessions with:
  - Full context restoration
  - Task progress tracking
  - Automatic file reference linking

- **Multi-Window Support**: Perfect for developers who:
  - Work on multiple projects simultaneously
  - Need to switch context frequently
  - Want to preserve work state across sessions

## Installation

### From GitHub (Recommended)

```bash
# Add the marketplace
/plugin marketplace add Claudate/claude-code-context-sync

# Install the plugin
/plugin install context-sync
```

### Update Plugin (Recommended)

To update the plugin to the latest version (easiest way):

```bash
# Simply reload the plugin
/plugin reload context-sync
```

Or if you want to pull the latest version from GitHub:

```bash
# Update to latest version
/plugin update context-sync
```

### Reinstallation (If Already Installed)

If you get an error saying the marketplace is already installed:

```bash
# Option 1: Just reload (quickest)
/plugin reload context-sync

# Option 2: Full reinstall (if reload doesn't work)
/plugin marketplace remove context-sync-marketplace
/plugin marketplace add Claudate/claude-code-context-sync
/plugin install context-sync
```

### Local Development

```bash
# Clone the repository
git clone https://github.com/Claudate/claude-code-context-sync.git

# Create a development marketplace
mkdir dev-marketplace
cp -r claude-code-context-sync dev-marketplace/

# Install locally in Claude Code
/plugin marketplace add ./dev-marketplace
/plugin install context-sync@dev-marketplace
```

## Usage

### Save Current Session

When you need to switch to another task or window:

```bash
/save-session
```

Or simply say:
```
换窗口处理-
```

The plugin will:
1. Analyze your current work context
2. Extract all tasks (completed and pending)
3. Save to `docs/context-sessions/YYYYMMDD-HHMM-description.md`

### Resume Previous Session

In a new window, restore your previous work:

```bash
/resume-session
```

The plugin will:
1. Show all available saved sessions
2. Let you select which one to resume
3. Load the full context and pending tasks
4. Help you continue from where you left off

### Example Workflow

```bash
# Window 1: Working on feature A
> Implementing user authentication...
> /save-session
✅ Context saved: docs/context-sessions/20251210-1430-user-auth.md

# Switch to Window 2: Work on bug fix
> Fixed critical bug in payment flow
> /save-session
✅ Context saved: docs/context-sessions/20251210-1500-payment-bug.md

# Back to Window 1 (or new window)
> /resume-session
📋 Available sessions:
1. 20251210-1430-user-auth.md (3 pending tasks)
2. 20251210-1500-payment-bug.md (1 pending task)

> Select: 1
📂 Loaded session: user-auth
🎯 Continuing with authentication implementation...
```

## Session File Format

Sessions are saved as markdown files in `docs/context-sessions/`:

```markdown
# Session: User Authentication Implementation

## 元信息
- **创建时间**: 2025-12-10 14:30
- **状态**: 进行中

## 上下文摘要
Implementing JWT-based authentication with refresh tokens...

## 已完成任务
- [x] Set up JWT library
- [x] Create auth middleware

## 未完成任务
- [ ] 🔴 高优先级: Implement token refresh logic
- [ ] 🟡 中优先级: Add password hashing
- [ ] 🟢 低优先级: Add OAuth integration

## 关键文件
- `backend/auth/jwt.service.ts` - JWT token management
- `backend/middleware/auth.middleware.ts` - Authentication middleware

## 注意事项
- Token expiry set to 1 hour
- Refresh tokens stored in httpOnly cookies

## 下一步行动
1. Review current JWT implementation
2. Add token refresh endpoint
3. Test with Postman
```

## Commands

| Command | Description |
|---------|-------------|
| `/save-session` | Save current work context |
| `/resume-session` | Resume a previous session |

## Skills

This plugin includes two AI skills that Claude can invoke automatically:

### `context-save`
Triggered when you say "换窗口处理-" or use `/save-session`. Analyzes the conversation and saves structured context.

### `context-resume`
Triggered with `/resume-session`. Lists available sessions and helps restore work context.

## Priority Markers

Tasks are marked with priority indicators:

| Marker | Priority | Use Case |
|--------|----------|----------|
| 🔴 | High | Blocking tasks, core features |
| 🟡 | Medium | Important but not urgent |
| 🟢 | Low | Nice-to-have, optimizations |

## Requirements

- Claude Code CLI
- Project must have a `docs/` directory (created automatically if missing)

## Configuration

No configuration needed! The plugin works out of the box.

Sessions are saved to `docs/context-sessions/` by default.

## Contributing

Contributions welcome! Please:

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

## License

MIT License - see [LICENSE](LICENSE) file for details

## Documentation

### Quick Links

- 📚 [Quick Reference Guide](QUICK_REFERENCE.md) - Common commands at a glance
- 🔧 [Troubleshooting Guide](TROUBLESHOOTING.md) - Solutions to common issues
- 🚀 [Quick Start Guide](QUICK_START.zh-CN.md) - Get started in 5 minutes

### Other Languages

- 🇨🇳 [简体中文](README.zh-CN.md)
- 📖 [All Languages](LANGUAGES.md)

## Support

- **Issues**: https://github.com/Claudate/claude-code-context-sync/issues
- **Discussions**: https://github.com/Claudate/claude-code-context-sync/discussions

## Changelog

### v1.0.0 (2025-12-10)

- Initial release
- Context save/resume functionality
- Slash command support
- Priority-based task tracking

## Credits

Developed by the Nano-AI Team for the Claude Code community.

---

**Made with ❤️ for Claude Code developers who juggle multiple tasks**
