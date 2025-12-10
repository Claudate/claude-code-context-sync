# 部署说明

本文档说明如何将 Context Sync 插件发布到 GitHub 并让其他用户安装。

## 前提条件

- GitHub 账号
- Git 已配置（用户名和邮箱）
- 已完成插件的本地开发和测试

## 发布步骤

### 1. 在 GitHub 创建新仓库

访问 https://github.com/new 创建新仓库：

```
仓库名称: claude-code-context-sync
描述: Save and resume Claude Code session context across multiple windows
可见性: Public
不要初始化 README、.gitignore 或 LICENSE（已存在）
```

### 2. 更新插件配置

在发布前，需要更新以下文件中的 GitHub 用户名：

**文件：** [.claude-plugin/plugin.json](.claude-plugin/plugin.json)

```json
{
  "homepage": "https://github.com/你的用户名/claude-code-context-sync#readme",
  "repository": "https://github.com/你的用户名/claude-code-context-sync"
}
```

**文件：** [.claude-plugin/marketplace.json](.claude-plugin/marketplace.json)

```json
{
  "plugins": [
    {
      "homepage": "https://github.com/你的用户名/claude-code-context-sync#readme",
      "repository": "https://github.com/你的用户名/claude-code-context-sync"
    }
  ]
}
```

### 3. 连接到远程仓库

```bash
cd claude-code-context-sync

# 添加远程仓库（替换为你的用户名）
git remote add origin https://github.com/你的用户名/claude-code-context-sync.git

# 推送到 GitHub
git branch -M main
git push -u origin main
```

### 4. 创建 Release（可选但推荐）

在 GitHub 仓库页面：

1. 点击 "Releases" → "Create a new release"
2. 标签版本: `v1.0.0`
3. 标题: `Context Sync v1.0.0 - Initial Release`
4. 描述:
   ```markdown
   ## Features
   - Save and resume session context across Claude Code windows
   - Priority-based task tracking
   - Slash commands for easy access

   ## Installation

   ```bash
   /plugin marketplace add 你的用户名/claude-code-context-sync
   /plugin install context-sync
   ```

   See [README](README.md) for detailed usage instructions.
   ```
5. 点击 "Publish release"

### 5. 让用户安装插件

用户现在可以通过以下方式安装：

**方法 1: 直接从仓库安装**

```bash
/plugin marketplace add 你的用户名/claude-code-context-sync
/plugin install context-sync
```

**方法 2: 克隆到本地安装**

```bash
git clone https://github.com/你的用户名/claude-code-context-sync.git
cd claude-code-context-sync

# 在 Claude Code 中
/plugin marketplace add ./claude-code-context-sync
/plugin install context-sync
```

## 更新插件

### 1. 修改代码

进行必要的更新和改进。

### 2. 更新版本号

**文件：** [.claude-plugin/plugin.json](.claude-plugin/plugin.json)

```json
{
  "version": "1.1.0"
}
```

**文件：** [CHANGELOG.md](CHANGELOG.md)

```markdown
## [1.1.0] - 2025-12-15

### Added
- 新功能描述

### Fixed
- 修复的问题
```

### 3. 提交并推送

```bash
git add .
git commit -m "chore: bump version to v1.1.0"
git push origin main
```

### 4. 创建新 Release

在 GitHub 创建新的 release（标签: `v1.1.0`）

用户可以通过以下命令更新：

```bash
/plugin update context-sync
```

## 推广插件

### 1. 添加 GitHub Topics

在 GitHub 仓库页面点击设置图标，添加以下 topics：

```
claude-code
claude-plugin
productivity
session-management
developer-tools
```

### 2. 社区分享

- 在 Claude Code Discord/社区分享
- 在相关论坛发布
- 撰写博客文章介绍使用方法

### 3. 完善文档

- 添加使用示例
- 录制演示视频
- 添加常见问题解答

## 维护指南

### 处理 Issues

- 及时回复用户问题
- 使用 GitHub Issues 追踪 bug
- 使用 labels 分类问题

### 接受 Pull Requests

1. 审查代码质量
2. 测试功能
3. 合并前更新 CHANGELOG.md
4. 感谢贡献者

## 故障排查

### 用户无法安装

**问题：** `/plugin marketplace add` 失败

**解决：**
- 确认仓库是 public
- 确认 `.claude-plugin/plugin.json` 存在
- 确认 JSON 格式正确

### 插件功能异常

**问题：** Skills 或 commands 不工作

**解决：**
- 检查文件路径是否正确
- 确认 SKILL.md 格式符合规范
- 查看 Claude Code 日志

## 联系方式

如有问题，请：

1. 查看 [README.md](README.md)
2. 搜索现有 Issues
3. 创建新 Issue：https://github.com/你的用户名/claude-code-context-sync/issues

---

**祝发布顺利！** 🚀
