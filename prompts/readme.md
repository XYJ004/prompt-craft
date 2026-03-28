# 📖 README 生成提示词

## 🎯 适用场景

- 新项目 README 创建
- 开源项目文档
- 项目文档标准化

---

## 💡 基础版提示词

```
请为我的项目生成一个专业的 README.md 文件。

## 项目信息
- 项目名称：[名称]
- 项目描述：[简短描述]
- 技术栈：[如 React, Node.js, MongoDB]
- 主要功能：[功能列表]

请包含：
1. 项目标题和简介
2. 功能特性
3. 安装步骤
4. 使用方法
5. 许可证
```

---

## 💡 进阶版提示词（推荐）

```
你是一位开源项目文档专家，请为我的项目生成一个高质量、专业且吸引人的 README.md 文件。

## 项目基本信息
- 项目名称：[名称]
- 一句话描述：[一句话说明项目是什么]
- 目标用户：[谁会使用这个项目]
- 核心价值：[解决什么问题]

## 技术信息
- 技术栈：[列出主要技术]
- 系统要求：[Node 版本、Python 版本等]
- 依赖：[主要依赖项]

## 功能列表
1. [功能 1]
2. [功能 2]
3. [功能 3]

## 安装/运行方式
[如 npm install, docker compose up 等]

## 使用示例
[希望展示的使用场景]

## 特殊要求
- [如：需要徽章、需要截图占位符、需要贡献指南]

## README 要求

请生成一个包含以下元素的完整 README：

### 必需部分
1. **标题区** - 项目名称 + 一句话描述 + 徽章
2. **简介** - 项目是什么，为什么需要它
3. **功能特性** - 3-6 个核心功能
4. **快速开始** - 安装和基本使用
5. **使用示例** - 常见使用场景
6. **贡献指南** - 如何贡献
7. **许可证** - 开源许可证

### 可选部分（根据项目类型添加）
- API 文档链接
- 配置说明
- 常见问题 FAQ
- 更新日志
- 致谢

### 格式要求
- 使用清晰的 Markdown 格式
- 代码块使用语法高亮
- 使用表格展示结构化信息
- 添加适当的 emoji 增强可读性
- 徽章使用 shields.io 风格

请直接输出 README.md 内容，不需要额外解释。
```

---

## 💡 GitHub 风格版

```
为我的 GitHub 项目创建一个 README.md，参考热门开源项目的风格。

项目：[项目名]
类型：[CLI工具/库/Web应用/API/其他]
描述：[描述]

请包含：
- 居中的标题和描述
- 徽章（License, Stars, Issues 等）
- 功能特性列表
- 安装命令
- 快速使用示例
- 配置选项
- 贡献方式
- 许可证

风格要求：
- 简洁专业
- 使用 emoji 增强可读性
- 代码示例清晰
- 结构层次分明
```

---

## 🌟 效果展示

**输入：**
```
项目名称：fast-api-cli
一句话描述：快速生成 RESTful API 项目的 CLI 工具
目标用户：后端开发者
核心价值：5秒创建标准化的 API 项目骨架
技术栈：Node.js, TypeScript, Express, Prisma
```

**输出：**
```markdown
<div align="center">

# 🚀 Fast API CLI

**5 秒创建标准化 RESTful API 项目骨架**

[![npm version](https://img.shields.io/npm/v/fast-api-cli?style=for-the-badge)](https://www.npmjs.com/package/fast-api-cli)
[![License](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)](LICENSE)
[![Stars](https://img.shields.io/github/stars/yourname/fast-api-cli?style=for-the-badge)](https://github.com/yourname/fast-api-cli)

</div>

---

## ✨ 功能特性

- 🏗️ **快速脚手架** - 一条命令创建完整项目结构
- 📦 **开箱即用** - 内置 TypeScript, ESLint, Prettier
- 🔌 **插件系统** - 支持数据库、认证等插件
- 📝 **代码生成** - 自动生成 CRUD 接口代码
- 🎯 **最佳实践** - 遵循行业标准的目录结构

## 📦 安装

```bash
# npm
npm install -g fast-api-cli

# yarn
yarn global add fast-api-cli

# pnpm
pnpm add -g fast-api-cli
```

## 🚀 快速开始

```bash
# 创建新项目
fast-api create my-api

# 进入项目目录
cd my-api

# 安装依赖
npm install

# 启动开发服务器
npm run dev
```

## 📖 文档

- [完整文档](docs/)
- [配置指南](docs/configuration.md)
- [插件开发](docs/plugins.md)

## 🤝 贡献

欢迎贡献！请查看 [贡献指南](CONTRIBUTING.md)

## 📄 许可证

[MIT](LICENSE) © 2024
```

---

## 📝 README 必备元素

| 元素 | 必要性 | 说明 |
|------|--------|------|
| 标题 + 描述 | ⭐⭐⭐ | 让人一眼知道项目是什么 |
| 徽章 | ⭐⭐ | 增加专业感和可信度 |
| 安装说明 | ⭐⭐⭐ | 用户必须知道如何安装 |
| 使用示例 | ⭐⭐⭐ | 最少一个可运行的示例 |
| 贡献指南 | ⭐ | 开源项目必备 |
| 许可证 | ⭐⭐ | 法律保护 |

---

## ⚠️ 注意事项

- 徽章图片需要实际存在的链接
- 截图/示例需要可运行
- 链接需要正确
- 更新 README 后同步更新其他文档

---

## 🔄 相关提示词

- [API 文档](api-docs.md)
- [代码注释](comments.md)
- [变更日志](changelog.md)
