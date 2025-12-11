# 快速参考 / Quick Reference

[English](#english) | [简体中文](#简体中文)

---

## English

### Installation & Updates

```bash
# First time installation
/plugin marketplace add Claudate/claude-code-context-sync
/plugin install context-sync

# Update plugin (easiest)
/plugin reload context-sync

# Update from GitHub
/plugin update context-sync

# Full reinstall (if needed)
/plugin marketplace remove context-sync-marketplace
/plugin marketplace add Claudate/claude-code-context-sync
/plugin install context-sync
```

### Daily Usage

```bash
# Save current session
/save-session

# Resume previous session
/resume-session

# Check installed plugins
/plugin list

# Check plugin info
/plugin info context-sync
```

### Troubleshooting

| Problem | Solution |
|---------|----------|
| Marketplace already installed | `/plugin reload context-sync` |
| Plugin already installed | `/plugin reload context-sync` |
| Want to update plugin | `/plugin update context-sync` |
| Plugin not working | `/plugin uninstall context-sync` then reinstall |

---

## 简体中文

### 安装与更新

```bash
# 首次安装
/plugin marketplace add Claudate/claude-code-context-sync
/plugin install context-sync

# 更新插件（最简单）
/plugin reload context-sync

# 从 GitHub 更新
/plugin update context-sync

# 完全重装（如需要）
/plugin marketplace remove context-sync-marketplace
/plugin marketplace add Claudate/claude-code-context-sync
/plugin install context-sync
```

### 日常使用

```bash
# 保存当前会话
/save-session

# 恢复之前的会话
/resume-session

# 查看已安装的插件
/plugin list

# 查看插件信息
/plugin info context-sync
```

### 故障排查

| 问题 | 解决方案 |
|------|----------|
| Marketplace 已安装 | `/plugin reload context-sync` |
| 插件已安装 | `/plugin reload context-sync` |
| 想要更新插件 | `/plugin update context-sync` |
| 插件不工作 | `/plugin uninstall context-sync` 然后重新安装 |

---

## Common Commands Comparison

| Task | Old Way (Complex) | New Way (Simple) |
|------|-------------------|------------------|
| Update plugin | Uninstall → Reinstall | `/plugin reload context-sync` |
| Fix marketplace error | Remove → Add → Install | `/plugin reload context-sync` |
| Get latest version | Full reinstall | `/plugin update context-sync` |

## 常用命令对比

| 任务 | 旧方法（复杂） | 新方法（简单） |
|------|---------------|---------------|
| 更新插件 | 卸载 → 重装 | `/plugin reload context-sync` |
| 修复 marketplace 错误 | 移除 → 添加 → 安装 | `/plugin reload context-sync` |
| 获取最新版本 | 完全重装 | `/plugin update context-sync` |

---

## Quick Tips

- 💡 **Fastest update**: Just use `/plugin reload context-sync`
- 📦 **Check before install**: Use `/plugin list` to see what's installed
- 🔄 **Auto-update**: Claude Code may auto-detect updates from GitHub
- 🆘 **Need help**: Check [TROUBLESHOOTING.md](TROUBLESHOOTING.md)

## 快速提示

- 💡 **最快更新方式**: 直接使用 `/plugin reload context-sync`
- 📦 **安装前检查**: 使用 `/plugin list` 查看已安装的内容
- 🔄 **自动更新**: Claude Code 可能会自动检测 GitHub 更新
- 🆘 **需要帮助**: 查看 [TROUBLESHOOTING.md](TROUBLESHOOTING.md)

---

**Last Updated**: 2025-12-11
