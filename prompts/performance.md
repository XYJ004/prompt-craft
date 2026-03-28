# ⚡ 性能优化提示词

## 🎯 适用场景

- 代码性能分析
- 性能瓶颈定位
- 优化方案设计
- 性能基准测试

---

## 💡 性能分析提示词

```
你是性能优化专家，请分析以下代码的性能问题并提供优化方案。

## 代码信息
- 语言/框架：[如 Python / Django]
- 运行环境：[如 AWS EC2 c5.xlarge]
- 数据规模：[如 100万用户]

## 待优化代码
```
[粘贴代码]
```

## 性能问题
[描述观察到的性能问题，如响应时间慢、内存占用高]

## 分析要求

1. **复杂度分析**
   - 时间复杂度
   - 空间复杂度
   - 瓶颈识别

2. **优化方案**
   - 算法优化
   - 数据结构优化
   - 缓存策略
   - 并发处理

3. **优化后代码**
   - 重写后的代码
   - 预期性能提升

4. **基准测试建议**
   - 测试方法
   - 关键指标
```

---

## 💡 数据库优化提示词

```
请帮我优化以下数据库查询。

## 数据库类型
[MySQL / PostgreSQL / MongoDB 等]

## 表结构
```sql
[表结构]
```

## 慢查询
```sql
[SQL 语句]
```

## 执行计划
[粘贴 EXPLAIN 结果]

## 数据规模
- 表行数：[如 1000万]
- 查询频率：[如 每秒 100 次]

请提供：
1. 索引优化建议
2. 查询重写
3. 分库分表建议（如需要）
4. 缓存策略
```

---

## 💡 前端性能优化提示词

```
分析并优化以下前端代码的性能。

## 技术栈
[如 React 18 / Vue 3 / 原生 JS]

## 问题描述
[如 首屏加载慢 / 列表滚动卡顿 / 内存泄漏]

## 代码
```javascript
[代码]
```

## 性能数据
- Lighthouse 得分：[如 60/100]
- 首屏时间：[如 3s]
- 包大小：[如 2MB]

请分析并提供优化方案：
1. 渲染优化
2. 资源优化
3. 网络优化
4. 代码分割建议
```

---

## 🌟 效果展示

**输入：**
```javascript
// 处理大数据集
function processData(data) {
  let result = [];
  for (let i = 0; i < data.length; i++) {
    for (let j = 0; j < data.length; j++) {
      if (data[i].id === data[j].parentId) {
        result.push({
          ...data[i],
          child: data[j]
        });
      }
    }
  }
  return result;
}
```

**输出：**
```
### 🔍 复杂度分析
- 时间复杂度：O(n²) - 嵌套循环
- 空间复杂度：O(n) - 结果数组
- 瓶颈：双重循环导致大数据集性能急剧下降

### ✅ 优化方案

**方案一：使用 Map 优化查找**
```javascript
function processData(data) {
  const parentMap = new Map();
  const result = [];
  
  // O(n) 建立索引
  data.forEach(item => {
    parentMap.set(item.id, item);
  });
  
  // O(n) 查找
  data.forEach(item => {
    if (item.parentId && parentMap.has(item.parentId)) {
      result.push({
        ...parentMap.get(item.parentId),
        child: item
      });
    }
  });
  
  return result;
}
```

**性能对比：**
| 数据量 | 优化前 | 优化后 | 提升 |
|--------|--------|--------|------|
| 1000 | 15ms | 1ms | 15x |
| 10000 | 1500ms | 10ms | 150x |
| 100000 | 超时 | 100ms | ∞ |

**时间复杂度：O(n²) → O(n)**
```

---

## 📝 常见性能优化模式

| 场景 | 优化方式 |
|------|----------|
| 循环嵌套 | Map/Set 索引 |
| 重复计算 | 缓存/Memo |
| 大数据渲染 | 虚拟列表 |
| 频繁请求 | 防抖/节流 |
| 大文件加载 | 懒加载/分片 |
| 数据库慢查询 | 索引优化 |

---

## 🔄 相关提示词

- [代码重构](refactor.md)
- [系统设计](system-design.md)
- [代码审查](code-review.md)
