# Context Sync - Claude Code 会话管理插件

[English](README.md) | 简体中文

在多个 Claude Code 窗口间保存和恢复会话上下文。工作进度不再丢失，随时切换任务无压力。

## 功能特性

- **智能上下文保存**：自动提取并保存：
  - 已完成和待办任务
  - 正在编辑的关键文件
  - 技术决策和注意事项
  - 基于优先级的任务组织

- **快速会话恢复**：恢复之前的工作时可以：
  - 完整还原上下文
  - 追踪任务进度
  - 自动关联文件引用

- **多窗口支持**：非常适合以下场景：
  - 同时开发多个项目
  - 需要频繁切换上下文
  - 希望保留跨会话的工作状态

## 安装

### 从 GitHub 安装（推荐）

```bash
# 添加插件市场
/plugin marketplace add Claudate/claude-code-context-sync

# 安装插件
/plugin install context-sync
```

### 更新插件（推荐）

更新插件到最新版本（最简单的方式）：

```bash
# 直接重新加载插件
/plugin reload context-sync
```

或者从 GitHub 拉取最新版本：

```bash
# 更新到最新版本
/plugin update context-sync
```

### 重新安装（如果已安装过）

如果遇到提示 marketplace 已经安装的错误：

```bash
# 方式 1: 直接重新加载（最快）
/plugin reload context-sync

# 方式 2: 完全重装（如果重新加载不生效）
/plugin marketplace remove context-sync-marketplace
/plugin marketplace add Claudate/claude-code-context-sync
/plugin install context-sync
```

### 本地开发安装

```bash
# 克隆仓库
git clone https://github.com/Claudate/claude-code-context-sync.git

# 创建开发市场
mkdir dev-marketplace
cp -r claude-code-context-sync dev-marketplace/

# 在 Claude Code 中安装
/plugin marketplace add ./dev-marketplace
/plugin install context-sync@dev-marketplace
```

## 使用方法

### 保存当前会话

当你需要切换到其他任务或窗口时：

```bash
/save-session
```

或者直接说：
```
换窗口处理-
```

插件会自动：
1. 分析当前工作上下文
2. 提取所有任务（已完成和待办）
3. 保存到 `docs/context-sessions/YYYYMMDD-HHMM-描述.md`

### 恢复之前的会话

在新窗口中恢复之前的工作：

```bash
/resume-session
```

插件会：
1. 显示所有可用的已保存会话
2. 让你选择要恢复的会话
3. 加载完整上下文和待办任务
4. 帮助你从中断处继续工作

### 使用示例

```bash
# 窗口 1：开发功能 A
> 正在实现用户认证功能...
> /save-session
✅ 上下文已保存到: docs/context-sessions/20251210-1430-用户认证.md

# 切换到窗口 2：修复紧急 bug
> 修复了支付流程中的关键 bug
> /save-session
✅ 上下文已保存到: docs/context-sessions/20251210-1500-支付bug.md

# 回到窗口 1（或新窗口）
> /resume-session
📋 可用的会话列表：
1. 20251210-1430-用户认证.md（3 个待办任务）
2. 20251210-1500-支付bug.md（1 个待办任务）

> 选择：1
📂 已加载会话：用户认证
🎯 继续实现认证功能...
```

## 会话文件格式

会话保存为 markdown 文件，位于 `docs/context-sessions/`：

```markdown
# Session: 用户认证功能实现

## 元信息
- **创建时间**: 2025-12-10 14:30
- **状态**: 进行中

## 上下文摘要
实现基于 JWT 的认证系统，包含 refresh token 机制...

## 已完成任务
- [x] 安装 JWT 库
- [x] 创建认证中间件

## 未完成任务
- [ ] 🔴 高优先级: 实现 token 刷新逻辑
- [ ] 🟡 中优先级: 添加密码加密
- [ ] 🟢 低优先级: 集成 OAuth

## 关键文件
- `backend/auth/jwt.service.ts` - JWT token 管理
- `backend/middleware/auth.middleware.ts` - 认证中间件

## 注意事项
- Token 过期时间设为 1 小时
- Refresh token 存储在 httpOnly cookie

## 下一步行动
1. 查看当前 JWT 实现
2. 添加 token 刷新端点
3. 使用 Postman 测试
```

## 命令

| 命令 | 说明 |
|------|------|
| `/save-session` | 保存当前工作上下文 |
| `/resume-session` | 恢复之前的会话 |

## Skills

本插件包含两个 AI skill，Claude 可以自动调用：

### `context-save`
当你说"换窗口处理-"或使用 `/save-session` 时触发。分析对话并保存结构化上下文。

### `context-resume`
使用 `/resume-session` 触发。列出可用会话并帮助恢复工作上下文。

## 优先级标记

任务标记有优先级指示器：

| 标记 | 优先级 | 使用场景 |
|------|--------|---------|
| 🔴 | 高 | 阻塞性任务、核心功能 |
| 🟡 | 中 | 重要但不紧急 |
| 🟢 | 低 | 锦上添花的功能、优化 |

## 系统要求

- Claude Code CLI
- 项目需要有 `docs/` 目录（如果不存在会自动创建）

## 配置

无需配置！插件开箱即用。

会话默认保存到 `docs/context-sessions/`。

## 贡献

欢迎贡献！请：

1. Fork 仓库
2. 创建功能分支
3. 提交你的更改
4. 发送 Pull Request

## 许可证

MIT License - 详见 [LICENSE](LICENSE) 文件

## 文档

### 快速链接

- 📚 [快速参考指南](QUICK_REFERENCE.md) - 常用命令速查
- 🔧 [故障排查指南](TROUBLESHOOTING.md) - 常见问题解决方案
- 🚀 [快速开始指南](QUICK_START.zh-CN.md) - 5 分钟上手

### 其他语言

- 🇺🇸 [English](README.md)
- 📖 [所有语言](LANGUAGES.md)

## 支持

- **Issues**: https://github.com/Claudate/claude-code-context-sync/issues
- **Discussions**: https://github.com/Claudate/claude-code-context-sync/discussions

## 更新日志

### v1.0.0 (2025-12-10)

- 首次发布
- 上下文保存/恢复功能
- 斜杠命令支持
- 基于优先级的任务追踪

## 致谢

由 Nano-AI Team 为 Claude Code 开发者社区开发。

---

**为同时处理多任务的 Claude Code 开发者用心打造** ❤️
