# 🔐 Git 提交信息提示词

## 🎯 适用场景

- 生成规范的 commit message
- 代码提交信息规范化
- 团队协作统一风格

---

## 💡 基础版提示词

```
请为以下代码变更生成 Git 提交信息。

## 变更内容
```
[粘贴 git diff 或变更描述]
```

请生成一条简洁明了的 commit message。
```

---

## 💡 进阶版提示词（推荐）

```
你是 Git 提交信息专家，请根据以下代码变更生成规范的 commit message。

## 变更类型
- [ ] feat: 新功能
- [ ] fix: 修复 bug
- [ ] docs: 文档更新
- [ ] style: 代码格式
- [ ] refactor: 重构
- [ ] test: 测试相关
- [ ] chore: 构建/工具

## 代码变更
```diff
[粘贴 git diff 内容]
```

## 变更背景
[可选：为什么做这个变更]

## Commit Message 规范

请按以下格式生成：

```
<type>(<scope>): <subject>

<body>

<footer>
```

### 格式说明

**type（必填）**：
- feat: 新功能
- fix: 修复 bug
- docs: 文档变更
- style: 代码格式（不影响功能）
- refactor: 重构
- perf: 性能优化
- test: 测试相关
- chore: 构建/工具/依赖

**scope（可选）**：影响范围，如 `user`, `order`, `api`

**subject（必填）**：
- 不超过 50 字符
- 使用动词开头
- 不以句号结尾
- 小写开头

**body（可选）**：
- 详细描述变更内容
- 说明为什么做这个变更
- 每行不超过 72 字符

**footer（可选）**：
- Breaking Changes: `BREAKING CHANGE:`
- 关闭 Issue: `Closes #123`

## 示例

```
feat(user): add password reset functionality

- Add password reset API endpoint
- Implement email verification
- Add rate limiting for reset requests

Closes #234
```

请生成 3 个备选 commit message。
```

---

## 💡 快速版

```
根据以下变更生成 commit message：

[变更描述或 diff]

格式：type(scope): subject
```

---

## 🌟 效果展示

**输入：**
```diff
+function validateEmail(email: string): boolean {
+  const regex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
+  return regex.test(email);
+}

-const user = await User.findById(id);
+const user = await User.findById(id).select('-password');
```

**输出：**
```
### 备选 1（推荐）
```
feat(auth): add email validation and hide password in user query

- Add validateEmail utility function with regex pattern
- Exclude password field from user query response
```

### 备选 2（简洁版）
```
feat(auth): improve user data handling

Add email validation and exclude password from queries
```

### 备选 3（详细版）
```
feat(auth): enhance user authentication utilities

- feat: add validateEmail function for email format validation
- fix: exclude password field from user query to prevent data leak

This commit improves security by not returning password in user
queries and adds a reusable email validation utility.
```
```

---

## 📝 Commit Message 模板库

### 功能开发
```
feat(module): add feature description

- Detail 1
- Detail 2
```

### Bug 修复
```
fix(module): fix bug description

Problem: [描述问题]
Solution: [描述解决方案]

Closes #issue-number
```

### 重构
```
refactor(module): refactor description

Before: [重构前]
After: [重构后]

Benefits:
- Improvement 1
- Improvement 2
```

### 性能优化
```
perf(module): optimize description

- Optimization 1
- Optimization 2

Benchmark:
- Before: XX ms
- After: XX ms
```

### 文档更新
```
docs: update documentation

- Update README
- Add API documentation
```

---

## ⚠️ 注意事项

- 不要写 "update code" 这种无意义信息
- 一个 commit 做一件事
- 大改动拆成多个 commit
- 使用英文，团队统一

---

## 🔄 相关提示词

- [代码审查](code-review.md)
- [README 生成](readme.md)
- [代码注释](comments.md)
