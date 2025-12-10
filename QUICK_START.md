# 快速开始指南

5 分钟学会使用 Context Sync 插件。

## 安装

```bash
# 方法 1: 从 GitHub 安装（推荐）
/plugin marketplace add Claudate/claude-code-context-sync
/plugin install context-sync

# 方法 2: 本地开发安装
git clone https://github.com/Claudate/claude-code-context-sync.git
/plugin marketplace add ./claude-code-context-sync
/plugin install context-sync
```

## 基本用法

### 场景 1: 保存当前工作进度

你正在开发用户认证功能，突然需要切换到另一个紧急任务：

```bash
# 在当前窗口
> 我正在实现 JWT 认证，已经完成了 token 生成，还需要添加刷新机制
> /save-session

✅ 上下文已保存到: docs/context-sessions/20251210-1430-jwt-auth.md

新窗口恢复方法:
1. 调用 /resume-session
2. 选择对应的 session 文件

未完成任务数: 3
```

### 场景 2: 恢复之前的工作

在新窗口或稍后继续之前的工作：

```bash
> /resume-session

📋 待处理的 Session 列表:

1. 20251210-1430-jwt-auth.md
   未完成任务: 3 项

2. 20251210-1500-payment-bug.md
   未完成任务: 1 项

请告诉我要恢复哪个 session（输入序号或文件名）

> 1

📂 已加载 Session: jwt-auth

# Session: JWT 认证实现

## 未完成任务
- [ ] 🔴 高优先级: 实现 token 刷新机制
- [ ] 🟡 中优先级: 添加密码加密
- [ ] 🟢 低优先级: 添加 OAuth 集成

🎯 接下来要处理哪个任务？或者需要我继续之前的工作？

> 继续实现 token 刷新机制
```

## 常用命令

| 命令 | 说明 | 示例 |
|------|------|------|
| `/save-session` | 保存当前会话 | 在任何时候保存工作进度 |
| `/resume-session` | 恢复之前的会话 | 列出并选择要恢复的 session |
| `换窗口处理-` | 自动触发保存 | 中文快捷指令 |

## 实用技巧

### 1. 任务优先级管理

使用优先级标记帮助你快速识别重要任务：

- 🔴 **高优先级**: 阻塞性任务、核心功能
- 🟡 **中优先级**: 重要但不紧急
- 🟢 **低优先级**: 优化、可选功能

### 2. 多项目并行工作

同时开发多个功能时，为每个功能创建独立的 session：

```bash
# 项目 A - 用户认证
> /save-session
✅ 保存到: 20251210-1430-user-auth.md

# 项目 B - 支付集成
> /save-session
✅ 保存到: 20251210-1500-payment-integration.md

# 项目 C - 性能优化
> /save-session
✅ 保存到: 20251210-1600-performance-opt.md
```

### 3. 工作交接

与团队成员分享 session 文件：

```bash
# 导出 session
cp docs/context-sessions/20251210-1430-feature-x.md /path/to/share/

# 同事可以导入并继续
cp /path/to/shared/20251210-1430-feature-x.md docs/context-sessions/
> /resume-session
```

## Session 文件示例

```markdown
# Session: 实现用户认证

## 元信息
- **创建时间**: 2025-12-10 14:30
- **状态**: 进行中

## 上下文摘要
实现基于 JWT 的用户认证系统，包括登录、注册、token 刷新。

## 已完成任务
- [x] 安装 jsonwebtoken 库
- [x] 创建 auth middleware
- [x] 实现 token 生成逻辑

## 未完成任务
- [ ] 🔴 高优先级: 实现 token 刷新端点
- [ ] 🔴 高优先级: 添加密码哈希
- [ ] 🟡 中优先级: 添加登录失败限制
- [ ] 🟢 低优先级: 集成 OAuth2

## 关键文件
- `backend/auth/jwt.service.ts` - JWT 服务
- `backend/middleware/auth.middleware.ts` - 认证中间件
- `backend/routes/auth.routes.ts` - 认证路由

## 注意事项
- Token 过期时间设为 1 小时
- Refresh token 存储在 httpOnly cookie
- 密码需要使用 bcrypt 加密

## 下一步行动
1. 阅读 jwt.service.ts 了解当前实现
2. 添加 /auth/refresh 端点
3. 测试 token 刷新流程
```

## 工作流程建议

### 开发流程

```
1. 开始新任务
   ↓
2. 工作一段时间
   ↓
3. 需要切换任务？
   ├─ 是 → /save-session → 切换到新任务
   └─ 否 → 继续工作
   ↓
4. 恢复之前任务
   ↓
5. /resume-session
   ↓
6. 选择 session 继续
   ↓
7. 完成所有任务后 session 自动删除
```

### 每日工作习惯

**上午：**
```bash
> /resume-session
# 查看昨天未完成的任务
# 继续开发
```

**工作中：**
```bash
# 随时保存重要进度
> /save-session
```

**下班前：**
```bash
> /save-session
# 确保工作进度已保存
# 第二天可以快速恢复
```

## 常见问题

### Q: Session 文件保存在哪里？

A: 保存在项目的 `docs/context-sessions/` 目录下。

### Q: 如何删除 session？

A: 当所有任务完成后自动删除，或手动删除文件：
```bash
rm docs/context-sessions/文件名.md
```

### Q: 可以在不同项目间使用吗？

A: 可以！每个项目都有独立的 `docs/context-sessions/` 目录。

### Q: Session 文件可以手动编辑吗？

A: 可以！它们是标准的 Markdown 文件，可以随时编辑。

## 下一步

- 阅读完整 [README.md](README.md) 了解所有功能
- 查看 [DEPLOYMENT.md](DEPLOYMENT.md) 了解如何发布插件
- 访问 GitHub Issues 报告问题或建议

---

**开始使用吧！** 现在就用 `/save-session` 保存你的第一个会话 🚀
