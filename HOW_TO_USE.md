# 如何使用 Context Sync 插件

## 重要说明 ⚠️

**插件已经生成完毕！** 推送到 GitHub 后，插件就可以被其他人安装和使用了。

Claude Code 的插件系统是**分布式的**，不需要提交到官方审核。用户直接从你的 GitHub 仓库安装即可。

---

## 插件已就绪 ✅

你的插件现在位于：
- **GitHub**: https://github.com/Claudate/claude-code-context-sync
- **状态**: 公开，可安装
- **版本**: v1.0.0

---

## 用户如何安装你的插件

### 第一步：添加市场

用户在 Claude Code 中执行：

```bash
/plugin marketplace add Claudate/claude-code-context-sync
```

这个命令会：
1. 从你的 GitHub 仓库读取 `.claude-plugin/marketplace.json`
2. 将你的插件市场添加到用户的 Claude Code

### 第二步：安装插件

```bash
/plugin install context-sync
```

这个命令会：
1. 下载你的插件文件到用户本地
2. 注册 skills 和 commands
3. 使插件立即可用

### 第三步：使用插件

```bash
# 保存当前会话
/save-session

# 恢复之前的会话
/resume-session
```

---

## 你现在可以做什么

### 1. 本地测试（推荐）

在你的电脑上测试插件是否正常工作：

```bash
# 在 Claude Code 中
/plugin marketplace add Claudate/claude-code-context-sync
/plugin install context-sync

# 测试保存功能
/save-session

# 测试恢复功能
/resume-session
```

### 2. 创建 GitHub Release（可选但推荐）

为了让用户更容易找到你的插件：

1. 访问 https://github.com/Claudate/claude-code-context-sync/releases/new
2. 填写以下信息：

```
Tag version: v1.0.0
Release title: Context Sync v1.0.0 - Initial Release

Description:
## 🎉 首次发布

智能的 Claude Code 会话管理插件。

### 安装

bash
/plugin marketplace add Claudate/claude-code-context-sync
/plugin install context-sync


### 功能

- 💾 保存会话上下文
- 🔄 恢复之前的工作
- 📋 任务优先级管理

查看 [README](https://github.com/Claudate/claude-code-context-sync#readme) 了解详细用法。
```

3. 点击 "Publish release"

### 3. 分享插件

**在社交媒体分享**：

```
🚀 刚发布了一个新的 Claude Code 插件！

Context Sync - 在多窗口间保存和恢复工作上下文

安装：
/plugin marketplace add Claudate/claude-code-context-sync
/plugin install context-sync

GitHub: https://github.com/Claudate/claude-code-context-sync

#ClaudeCode #Productivity
```

**在技术社区分享**：
- Claude Discord
- Reddit r/ClaudeAI
- Hacker News
- Dev.to

### 4. 添加 README Badge（可选）

在 README.md 顶部添加徽章：

```markdown
# Context Sync Plugin

[![GitHub release](https://img.shields.io/github/v/release/Claudate/claude-code-context-sync)](https://github.com/Claudate/claude-code-context-sync/releases)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Claude Code](https://img.shields.io/badge/Claude_Code-Plugin-blue.svg)](https://claude.com/claude-code)
```

---

## 常见问题

### Q: 插件需要审核吗？

**A**: 不需要！Claude Code 采用分布式市场，任何人都可以发布插件。用户直接从你的 GitHub 仓库安装。

### Q: 如何更新插件？

**A**:
1. 修改代码
2. 更新 `plugin.json` 中的版本号
3. 更新 `CHANGELOG.md`
4. 提交并推送到 GitHub
5. 创建新的 GitHub Release

用户可以通过以下命令更新：
```bash
/plugin update context-sync
```

### Q: 如何追踪有多少人在使用？

**A**:
- 查看 GitHub Stars 数量
- 查看 GitHub Clone 统计
- 关注 Issues 和 Discussions

### Q: 插件无法安装怎么办？

**A**: 检查：
1. 仓库是否为 Public
2. `.claude-plugin/plugin.json` 是否存在且格式正确
3. 文件路径是否正确
4. JSON 是否有语法错误

---

## 插件工作原理

### 文件结构

```
你的 GitHub 仓库
    ↓
用户执行 /plugin marketplace add
    ↓
Claude Code 读取 .claude-plugin/marketplace.json
    ↓
用户执行 /plugin install context-sync
    ↓
Claude Code 下载插件文件到本地
    ↓
注册 skills 和 commands
    ↓
用户可以使用 /save-session 和 /resume-session
```

### Skills 如何工作

当用户说"换窗口处理-"时：
1. Claude 识别到触发词
2. 调用 `context-save` skill
3. 执行 SKILL.md 中定义的步骤
4. 保存 session 文件到 `docs/context-sessions/`

### Commands 如何工作

当用户输入 `/save-session` 时：
1. Claude Code 读取 `commands/save-session.md`
2. 执行其中的指令（调用相应的 skill）
3. 返回结果给用户

---

## 监控和维护

### 查看插件使用情况

1. **GitHub Insights**
   - 访问：https://github.com/Claudate/claude-code-context-sync/pulse
   - 查看：Clones, Visitors, Traffic

2. **Issues 管理**
   - 及时回复用户问题
   - 使用 labels 分类
   - 记录 bug 和功能请求

3. **Discussions**
   - 启用 GitHub Discussions
   - 与用户交流
   - 收集反馈和建议

### 版本发布流程

```bash
# 1. 修改代码
vim skills/context-save/SKILL.md

# 2. 更新版本号
vim .claude-plugin/plugin.json
# 改为 "version": "1.1.0"

# 3. 更新日志
vim CHANGELOG.md
# 添加新版本的更改

# 4. 提交
git add .
git commit -m "feat: add new feature xyz"
git push

# 5. 创建 GitHub Release
# 访问 GitHub 创建 v1.1.0 release
```

---

## 下一步建议

### 立即行动
1. ✅ **本地测试插件**
   ```bash
   /plugin marketplace add Claudate/claude-code-context-sync
   /plugin install context-sync
   /save-session
   ```

2. ✅ **创建 GitHub Release**
   - 访问 releases 页面
   - 创建 v1.0.0 release

3. ✅ **添加 Topics**
   - claude-code
   - claude-plugin
   - productivity

### 短期目标（1周内）
- 📢 在社交媒体分享
- 📝 撰写使用教程
- 🎥 录制演示视频（可选）

### 中期目标（1月内）
- 📊 收集用户反馈
- 🐛 修复发现的 bug
- ✨ 规划新功能

---

## 恭喜！🎉

你的插件已经成功发布！现在任何 Claude Code 用户都可以安装和使用它。

**插件安装命令**：
```bash
/plugin marketplace add Claudate/claude-code-context-sync
/plugin install context-sync
```

祝你的插件获得成功！ 🚀

---

*如有问题，请在 GitHub Issues 中提问：*
https://github.com/Claudate/claude-code-context-sync/issues
