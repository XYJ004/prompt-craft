# 🔧 代码重构提示词

## 🎯 适用场景

- 代码质量提升
- 技术债务清理
- 性能优化重构
- 代码可维护性改进

---

## 💡 基础版提示词

```
请帮我重构以下代码，使其更加清晰、高效、可维护。

代码语言：[语言]
原始代码：
```
[代码]
```

重构目标：
- 提高可读性
- 减少重复
- 遵循最佳实践
- 保持功能不变

请提供：
1. 重构后的代码
2. 改进点说明
```

---

## 💡 进阶版提示词（推荐）

```
你是一位拥有 20 年经验的软件架构师，擅长代码重构和设计模式。请对以下代码进行专业重构：

## 原始代码信息
- 语言/框架：[如 Java 17 / Spring Boot]
- 代码位置：[如 UserService.java]
- 代码用途：[简述功能]

## 原始代码
```
[粘贴代码]
```

## 重构目标
请根据以下原则进行重构：

### 1. SOLID 原则
- 单一职责：每个类/函数只做一件事
- 开闭原则：对扩展开放，对修改关闭
- 里氏替换：子类可以替换父类
- 接口隔离：接口最小化
- 依赖倒置：依赖抽象而非具体

### 2. 设计模式应用
- 识别可应用的设计模式
- 说明为什么适用
- 展示如何应用

### 3. 代码质量提升
- DRY（不重复）
- KISS（保持简单）
- YAGNI（不做不需要的）
- 命名清晰
- 注释适当

### 4. 性能考量
- 时间复杂度
- 空间复杂度
- 潜在瓶颈

## 输出格式

### 🔴 重构前问题分析
| 问题类型 | 位置 | 描述 | 严重程度 |
|----------|------|------|----------|
| 违反单一职责 | UserService | 同时处理用户和订单 | 高 |

### 🟢 重构方案
**整体策略：** [描述重构思路]

**关键改动：**

1. **[改动点 1]**
   - 原因：
   - 方案：
```[重构后代码]```

2. **[改动点 2]**
   - 原因：
   - 方案：
```[重构后代码]```

### 📊 重构对比

| 指标 | 重构前 | 重构后 | 改进 |
|------|--------|--------|------|
| 行数 | 150 | 100 | -33% |
| 圈复杂度 | 12 | 4 | -67% |
| 可测试性 | 低 | 高 | ✓ |

### 🎯 应用设计模式
- 模式：[如 工厂模式]
- 原因：[为什么适用]
- 效果：[带来的好处]

### ⚠️ 重构注意事项
- [需要注意的点]
- [可能的副作用]
```

---

## 💡 快速重构版

```
重构这段代码，使其更简洁高效：

```
[代码]
```

要求：
1. 减少重复
2. 提高可读性
3. 遵循 [语言] 最佳实践
4. 保持功能不变
```

---

## 🌟 效果展示

**输入：**
```javascript
function calculatePrice(items, user) {
  let total = 0;
  for (let i = 0; i < items.length; i++) {
    if (items[i].type === 'normal') {
      total += items[i].price * items[i].quantity;
    } else if (items[i].type === 'discount') {
      total += items[i].price * items[i].quantity * 0.9;
    } else if (items[i].type === 'premium') {
      total += items[i].price * items[i].quantity * 0.8;
    }
  }
  if (user.level === 'vip') {
    total = total * 0.95;
  } else if (user.level === 'svip') {
    total = total * 0.9;
  }
  return total;
}
```

**输出：**
```javascript
// 重构后
const ITEM_TYPE_DISCOUNTS = {
  normal: 1.0,
  discount: 0.9,
  premium: 0.8,
};

const USER_LEVEL_DISCOUNTS = {
  vip: 0.95,
  svip: 0.9,
  normal: 1.0,
};

function calculateItemPrice(item) {
  const discount = ITEM_TYPE_DISCOUNTS[item.type] ?? 1.0;
  return item.price * item.quantity * discount;
}

function applyUserDiscount(total, user) {
  const discount = USER_LEVEL_DISCOUNTS[user.level] ?? 1.0;
  return total * discount;
}

function calculatePrice(items, user) {
  const subtotal = items.reduce(
    (sum, item) => sum + calculateItemPrice(item),
    0
  );
  return applyUserDiscount(subtotal, user);
}
```

**改进点：**
- 消除魔法数字，使用常量配置
- 提取纯函数，单一职责
- 使用 reduce 替代 for 循环
- 增加可读性和可测试性
```

---

## ⚠️ 注意事项

- 重构前确保有测试覆盖
- 小步重构，逐步验证
- 保持向后兼容
- 记录重构原因

---

## 🔄 相关提示词

- [代码审查](code-review.md)
- [性能优化](performance.md)
- [单元测试](unit-test.md)
