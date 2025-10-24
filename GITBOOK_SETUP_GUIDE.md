# GitBook 设置指南

本指南将帮助你快速将此 GitHub 仓库连接到 GitBook。

## 📋 前提条件

- ✅ GitHub 账号
- ✅ 本仓库已推送到 GitHub
- ✅ GitBook 账号（如果没有，可以使用 GitHub 登录）

## 🚀 快速设置步骤

### 第一步：访问 GitBook

1. 打开浏览器，访问 https://www.gitbook.com/
2. 点击右上角 "Sign in"
3. 选择 "Sign in with GitHub"（推荐）

### 第二步：创建新 Space

1. 登录后，点击 "New Space" 或 "Create a new space"
2. 选择 "Import" 方式
3. 选择 "GitHub" 作为源

### 第三步：连接 GitHub 仓库

1. 首次使用需要授权 GitBook 访问 GitHub
   - 点击 "Install GitHub App"
   - 选择要授权的组织或个人账号
   - 可以选择授权所有仓库或特定仓库（建议选择特定仓库）

2. 授权完成后，选择仓库：
   - 仓库：`godlovericea/test-gitbook-doc`
   - 分支：`main`（默认）

3. GitBook 会自动检测 `.gitbook.yaml` 配置

### 第四步：配置同步选项

选择同步方式：

#### 选项 A：单向同步（推荐用于测试）
```
GitHub → GitBook
- 只从 GitHub 读取
- 在 Git 中修改，GitBook 自动更新
```

#### 选项 B：双向同步
```
GitHub ⟷ GitBook
- 可以在 GitBook 网页编辑
- 编辑会自动提交回 GitHub
```

**建议**：测试阶段使用单向同步，避免冲突。

### 第五步：导入并发布

1. 点击 "Import" 开始导入
2. 等待 1-2 分钟，GitBook 会构建你的文档
3. 完成后会自动跳转到文档页面

## ✅ 验证设置

### 检查文档结构

导入成功后，你应该看到：

- **首页**：Welcome/Introduction
- **Getting Started** 分类
  - Quick Start
  - Installation
- **Guides** 分类
  - Basic Guide
  - Advanced Topics
- **API Reference** 分类
  - API Overview
  - Authentication

### 测试搜索功能

1. 点击搜索框（快捷键：`Ctrl+K` 或 `Cmd+K`）
2. 输入关键词，如 "installation"
3. 查看搜索结果

### 检查 GitBook 特性

本文档已包含以下 GitBook 特性供测试：

- ✅ 提示框（Hint boxes）
- ✅ 代码高亮
- ✅ 多层级导航
- ✅ 内部链接
- ✅ 表格
- ✅ 任务列表
- ✅ 表情符号

## 🎨 自定义配置

### 配置域名（可选）

1. 进入 Space Settings
2. 点击 "Domain"
3. 添加自定义域名或使用 GitBook 子域名
   - 默认：`your-space.gitbook.io`
   - 自定义：`docs.yourdomain.com`

### 配置外观

1. Space Settings → Appearance
2. 自定义：
   - Logo
   - 配色方案
   - 字体

### 配置访问权限

1. Space Settings → Share
2. 选择：
   - **Public**：所有人可访问（推荐用于测试）
   - **Private**：仅邀请的成员可访问

## 🔄 更新文档

### 方法一：通过 Git（推荐）

```bash
# 在本地修改文档
cd test-gitbook-doc
code getting-started/quick-start.md

# 提交并推送
git add .
git commit -m "docs: update quick start guide"
git push origin main

# GitBook 会在 2-5 分钟内自动同步
```

### 方法二：GitBook 网页编辑（需双向同步）

1. 在 GitBook 中点击 "Edit"
2. 选择要编辑的页面
3. 使用所见即所得编辑器修改
4. 点击 "Save" 或 "Merge"

## 🧪 测试功能清单

- [ ] 文档成功导入到 GitBook
- [ ] 导航结构正确显示
- [ ] 搜索功能正常工作
- [ ] 代码块正确高亮
- [ ] 提示框正确显示
- [ ] 内部链接可以跳转
- [ ] 从 Git 推送能自动同步
- [ ] （可选）GitBook 编辑能同步回 Git

## 🔍 AI 功能测试（需付费版）

如果你有 GitBook Plus 或 Pro 版本：

### 启用 AI

1. Space Settings → AI
2. 开启 "GitBook AI"
3. 配置 AI 行为

### 测试 AI 搜索

在搜索框中尝试：

```
问题 1: "How do I install?"
问题 2: "What authentication methods are supported?"
问题 3: "Explain the API rate limits"
```

AI 应该能理解上下文并给出相关答案。

## 📊 查看分析数据

1. Space Settings → Insights
2. 查看：
   - 页面浏览量
   - 搜索查询
   - 热门内容
   - 用户行为

## ⚠️ 常见问题

### Q: GitBook 没有检测到配置？

**A**: 确保：
- `.gitbook.yaml` 在仓库根目录
- `README.md` 和 `SUMMARY.md` 存在
- YAML 语法正确（无 Tab，使用空格）

### Q: 导入后文档显示不正确？

**A**: 检查：
- `SUMMARY.md` 中的链接路径是否正确
- 所有引用的文件都已存在
- Markdown 格式是否正确

### Q: 如何删除测试内容？

**A**: 
1. 在 Space Settings → Danger Zone
2. 点击 "Delete Space"

## 🎯 对比测试建议

### 与 Docusaurus 对比要点

| 测试项 | GitBook | Docusaurus |
|--------|---------|-----------|
| 设置时间 | ⏱️ 记录时间 | ⏱️ 已知 |
| 易用性 | 📝 体验评分 | 📝 已知 |
| 搜索质量 | 🔍 测试几个查询 | 🔍 对比 |
| AI 功能 | 🤖 测试（如果有） | 🤖 对比 |
| 自定义能力 | 🎨 尝试定制 | 🎨 对比 |
| 编辑体验 | ✏️ 网页 vs 代码 | ✏️ 对比 |

### 记录测试结果

创建一个测试结果文档：

```markdown
# GitBook 测试结果

## 设置体验
- 时间：__分钟
- 难度：⭐⭐⭐⭐⭐ (1-5星)
- 问题：

## 功能测试
- 搜索：
- 导航：
- 编辑：
- AI：

## 总体印象
- 优点：
- 缺点：
- 适用场景：
```

## 📚 相关资源

- [GitBook 官方文档](https://docs.gitbook.com/)
- [GitHub 集成指南](https://docs.gitbook.com/integrations/git-sync)
- [GitBook vs Docusaurus 对比](../biya-coin-docs/GITBOOK_VS_DOCUSAURUS.md)

## 🆘 需要帮助？

如果遇到问题：

1. 查看 [GitBook 官方文档](https://docs.gitbook.com/)
2. 检查 [GitHub Issues](https://github.com/godlovericea/test-gitbook-doc/issues)
3. 联系我们

---

**祝测试顺利！** 🚀

记得记录你的测试体验，这将帮助我们做出最佳选择。

