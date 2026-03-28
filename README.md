<div align="center">

# 🚀 Prompt Craft

### 精心打磨的开发者 AI 提示词库 | Curated AI Prompts for Developers

**让 AI 成为你的编程搭档**

[![GitHub stars](https://img.shields.io/github/stars/XYJ004/prompt-craft?style=for-the-badge&logo=github&color=yellow)](https://github.com/XYJ004/prompt-craft/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/XYJ004/prompt-craft?style=for-the-badge&logo=github&color=blue)](https://github.com/XYJ004/prompt-craft/fork)
[![License](https://img.shields.io/badge/License-CC0--1.0-green?style=for-the-badge)](LICENSE)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen?style=for-the-badge)](CONTRIBUTING.md)

<img src="https://user-images.githubusercontent.com/placeholder/banner.png" width="800">

**中文版** | [English](README_EN.md)

</div>

---

## ✨ 为什么选择 Awesome Dev Prompts？

| 🎯 **场景驱动** | 🇨🇳 **中文优先** | ⚡ **即刻可用** | 🔄 **持续更新** |
|:---:|:---:|:---:|:---:|
| 按真实开发场景分类 | 专为中文开发者优化 | 复制粘贴直接使用 | 紧跟 AI 发展趋势 |

---

## 📚 提示词分类

### 🔧 代码质量

| 场景 | 提示词 | 效果 |
|------|--------|------|
| [代码审查](prompts/code-review.md) | 专业的代码审查助手 | 发现潜在问题、提升代码质量 |
| [代码重构](prompts/refactor.md) | 智能重构建议 | 优化代码结构、提升可维护性 |
| [代码解释](prompts/explain.md) | 通俗易懂的代码解读 | 快速理解复杂代码 |
| [Bug 调试](prompts/debug.md) | 系统化调试助手 | 快速定位和修复问题 |

### 📝 文档生成

| 场景 | 提示词 | 效果 |
|------|--------|------|
| [README 生成](prompts/readme.md) | 自动生成项目文档 | 美观专业的 README |
| [API 文档](prompts/api-docs.md) | 接口文档自动生成 | 标准 API 文档格式 |
| [注释生成](prompts/comments.md) | 智能代码注释 | 清晰的代码注释 |
| [变更日志](prompts/changelog.md) | 版本变更记录 | 规范的 CHANGELOG |

### 🧪 测试相关

| 场景 | 提示词 | 效果 |
|------|--------|------|
| [单元测试](prompts/unit-test.md) | 测试用例生成 | 全面的测试覆盖 |
| [集成测试](prompts/integration-test.md) | 集成测试设计 | 端到端测试方案 |
| [测试数据](prompts/test-data.md) | 测试数据生成 | 真实的测试数据 |

### 🏗️ 架构设计

| 场景 | 提示词 | 效果 |
|------|--------|------|
| [系统设计](prompts/system-design.md) | 架构设计助手 | 可扩展的架构方案 |
| [技术选型](prompts/tech-choice.md) | 技术栈建议 | 科学的技术决策 |
| [性能优化](prompts/performance.md) | 性能调优指南 | 系统性能提升 |

### ✍️ 文档写作

| 场景 | 提示词 | 效果 |
|------|--------|------|
| [技术文档](prompts/tech-writing.md) | 专业技术写作 | 清晰易懂的技术文档 |
| [README 生成](prompts/readme.md) | 自动生成项目文档 | 美观专业的 README |
| [Git 提交](prompts/commit-message.md) | 规范的提交信息 | 团队协作统一风格 |

### 🛡️ 安全相关

| 场景 | 提示词 | 效果 |
|------|--------|------|
| [安全审计](prompts/security-audit.md) | 代码安全检查 | 发现安全漏洞 |
| [SQL 注入检测](prompts/sql-injection.md) | 注入漏洞扫描 | 防止 SQL 注入 |
| [XSS 防护](prompts/xss-protection.md) | XSS 漏洞检测 | 前端安全加固 |

---

## 🚀 快速开始

### 方式一：直接使用

```bash
# 克隆仓库
git clone https://github.com/XYJ004/prompt-craft.git

# 浏览提示词
cd prompt-craft/prompts
```

### 方式二：在线浏览

直接在 GitHub 上浏览 [prompts/](prompts/) 目录，找到你需要的提示词。

### 方式三：作为 MCP 服务器

```json
{
  "mcpServers": {
    "dev-prompts": {
      "command": "npx",
      "args": ["prompt-craft", "mcp"]
    }
  }
}
```

---

## 📖 使用示例

### 代码审查提示词

```
你是一位资深代码审查专家。请审查以下代码，重点关注：

1. **潜在 Bug**: 是否有逻辑错误、边界情况未处理
2. **性能问题**: 是否有性能瓶颈、资源泄漏
3. **安全问题**: 是否有 SQL 注入、XSS 等漏洞
4. **代码规范**: 是否符合最佳实践、命名规范
5. **可维护性**: 代码是否易于理解和修改

请用中文回复，格式如下：
- 🔴 严重问题：...
- 🟡 建议改进：...
- 🟢 做得好的地方：...
```

**效果**：结构化的代码审查结果，一目了然。

---

## 🤝 贡献指南

我们欢迎所有形式的贡献！

### 贡献方式

1. **提交新提示词** - 在 `prompts/` 目录添加新文件
2. **改进现有提示词** - 优化提示词效果
3. **分享使用案例** - 在 `examples/` 分享你的经验
4. **翻译** - 帮助翻译成其他语言

### 提交规范

```bash
# 1. Fork 本仓库
# 2. 创建分支
git checkout -b feature/your-prompt-name

# 3. 添加提示词
# 在 prompts/ 目录创建 .md 文件

# 4. 提交
git commit -m "feat: add your-prompt-name prompt"

# 5. 推送并创建 PR
git push origin feature/your-prompt-name
```

---

## 📜 提示词模板

创建新提示词时，请使用以下模板：

```markdown
# [提示词名称]

## 🎯 适用场景
- 场景 1
- 场景 2

## 💡 提示词
\`\`\`
[你的提示词内容]
\`\`\`

## 📝 使用说明
1. 复制提示词
2. 替换占位符
3. 发送给 AI

## 🌟 效果展示
[可选：展示实际使用效果]

## ⚠️ 注意事项
- 注意点 1
- 注意点 2
```

---

## 🏆 致谢

- 感谢所有贡献者
- 灵感来源：[awesome-chatgpt-prompts](https://github.com/f/awesome-chatgpt-prompts)
- 所有支持本项目的 Star 用户 ⭐

---

## 📄 许可证

[CC0-1.0 License](LICENSE) - 自由使用，无需署名

---

<div align="center">

**如果这个项目对你有帮助，请给一个 ⭐ Star！**

[![Star History Chart](https://api.star-history.com/svg?repos=XYJ004/prompt-craft&type=Date)](https://star-history.com/#XYJ004/prompt-craft&Date)

**Made with ❤️ by [XYJ004](https://github.com/XYJ004)**

</div>
