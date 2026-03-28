# 🧪 单元测试生成提示词

## 🎯 适用场景

- 自动生成测试用例
- 提高测试覆盖率
- TDD 测试先行
- 测试用例补充

---

## 💡 基础版提示词

```
请为以下代码生成单元测试。

代码语言：[语言]
测试框架：[如 Jest / pytest / JUnit]

代码：
```
[粘贴代码]
```

请生成：
1. 正常情况的测试
2. 边界情况测试
3. 异常情况测试
```

---

## 💡 进阶版提示词（推荐）

```
你是一位测试驱动开发专家，请为以下代码生成全面、高质量的单元测试。

## 代码信息
- 语言/框架：[如 TypeScript / React]
- 测试框架：[如 Jest / Vitest]
- 测试风格：[如 AAA 模式 / BDD 风格]

## 待测试代码
```
[粘贴代码]
```

## 测试要求

### 覆盖维度

1. **功能测试**
   - 正常输入，预期输出
   - 多种有效输入组合
   - 边界值测试

2. **异常测试**
   - 无效输入
   - 空值/null/undefined
   - 类型错误
   - 超出范围

3. **边界测试**
   - 最小值、最大值
   - 空数组/空字符串
   - 临界点

4. **行为验证**
   - 函数调用次数
   - 参数验证
   - 副作用检查

### 测试原则

- 每个测试只验证一个行为
- 测试名称清晰描述测试内容
- 使用 AAA 模式（Arrange-Act-Assert）
- Mock 外部依赖
- 测试独立，不依赖执行顺序

## 输出格式

### 测试文件
```[语言]
[完整测试代码]
```

### 测试覆盖说明

| 函数/方法 | 测试场景 | 断言数量 |
|-----------|----------|----------|
| calculatePrice | 正常计算、折扣计算、空数组 | 3 |

### 运行说明
```bash
[测试运行命令]
```
```

---

## 💡 快速版

```
为这段 [语言] 代码生成单元测试，使用 [测试框架]：

```
[代码]
```

覆盖：正常、边界、异常情况。
```

---

## 🌟 效果展示

**输入：**
```typescript
function validateEmail(email: string): boolean {
  if (!email || typeof email !== 'string') {
    return false;
  }
  const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
  return emailRegex.test(email);
}
```

**输出：**
```typescript
import { validateEmail } from './validateEmail';

describe('validateEmail', () => {
  // 正常情况
  describe('valid emails', () => {
    it('should return true for standard email', () => {
      expect(validateEmail('test@example.com')).toBe(true);
    });

    it('should return true for email with subdomain', () => {
      expect(validateEmail('test@mail.example.com')).toBe(true);
    });

    it('should return true for email with numbers', () => {
      expect(validateEmail('test123@example.com')).toBe(true);
    });
  });

  // 边界情况
  describe('edge cases', () => {
    it('should return false for empty string', () => {
      expect(validateEmail('')).toBe(false);
    });

    it('should return false for email without @', () => {
      expect(validateEmail('testexample.com')).toBe(false);
    });

    it('should return false for email without domain', () => {
      expect(validateEmail('test@')).toBe(false);
    });

    it('should return false for email with multiple @', () => {
      expect(validateEmail('test@@example.com')).toBe(false);
    });

    it('should return false for email with spaces', () => {
      expect(validateEmail('test @example.com')).toBe(false);
    });
  });

  // 异常情况
  describe('invalid inputs', () => {
    it('should return false for null', () => {
      expect(validateEmail(null as any)).toBe(false);
    });

    it('should return false for undefined', () => {
      expect(validateEmail(undefined as any)).toBe(false);
    });

    it('should return false for number', () => {
      expect(validateEmail(123 as any)).toBe(false);
    });

    it('should return false for object', () => {
      expect(validateEmail({} as any)).toBe(false);
    });
  });
});
```

**测试覆盖说明：**
| 场景 | 测试数量 | 覆盖率 |
|------|----------|--------|
| 正常邮箱 | 3 | 100% |
| 边界情况 | 5 | 100% |
| 异常输入 | 4 | 100% |

---

## 📝 测试命名规范

```javascript
// 好的命名
it('should return false when email is empty', () => {});
it('should apply 10% discount for VIP users', () => {});

// 不好的命名
it('test1', () => {});
it('works', () => {});
```

---

## ⚠️ 注意事项

- Mock 外部依赖（API、数据库、文件系统）
- 测试应该快速执行
- 避免测试私有方法
- 保持测试独立

---

## 🔄 相关提示词

- [集成测试](integration-test.md)
- [测试数据生成](test-data.md)
- [Bug 调试](debug.md)
