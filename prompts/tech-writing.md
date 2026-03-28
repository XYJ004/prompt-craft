# 📝 技术文档写作提示词

## 🎯 适用场景

- API 文档编写
- 技术方案文档
- 技术博客文章
- 内部 Wiki 文档

---

## 💡 基础版提示词

```
请帮我写一份技术文档。

## 主题
[文档主题]

## 受众
[读者是谁：如 初级开发者/架构师/产品经理]

## 内容要点
1. [要点 1]
2. [要点 2]
3. [要点 3]

请写一篇结构清晰、通俗易懂的技术文档。
```

---

## 💡 进阶版提示词（推荐）

```
你是一位资深技术写作专家，擅长将复杂的技术概念转化为清晰易懂的文档。请为以下内容撰写技术文档。

## 文档信息
- 标题：[文档标题]
- 类型：[教程/API 文档/技术方案/最佳实践]
- 受众：[初级开发者/中级工程师/架构师/全员]
- 预计阅读时间：[如 10 分钟]

## 核心内容
[描述要文档化的技术内容]

## 写作要求

### 结构要求
1. **引言**（100-200字）
   - 背景介绍
   - 解决什么问题
   - 适用场景

2. **核心概念**（300-500字）
   - 关键术语解释
   - 原理说明
   - 架构图/流程图

3. **实践指南**（主要部分）
   - 环境准备
   - 分步骤实现
   - 完整代码示例
   - 常见问题

4. **最佳实践**（200-300字）
   - 推荐做法
   - 避坑指南
   - 性能优化

5. **总结**
   - 要点回顾
   - 扩展阅读

### 写作风格
- 使用第二人称（你）
- 短句为主，避免长句
- 代码示例完整可运行
- 配图说明复杂概念
- 重要信息加粗或用提示框

### 格式规范
- 使用 Markdown 格式
- 代码块指定语言高亮
- 表格对齐
- 标题层级清晰（最多 4 级）

## 特殊需求
- [如：需要英文版]
- [如：需要 PDF 导出格式]
```

---

## 💡 技术博客版

```
写一篇技术博客文章，主题是：[主题]

要求：
1. 标题吸引人
2. 开头有悬念或痛点
3. 有代码示例
4. 有实际应用场景
5. 结尾有总结和思考

风格：轻松、专业、有深度
字数：2000-3000 字
```

---

## 🌟 效果展示

**输入：**
```
主题：Redis 分布式锁实现
类型：教程
受众：中级开发者
```

**输出：**
```markdown
# Redis 分布式锁：从入门到实战

> 10 分钟掌握分布式锁的核心原理与最佳实践

## 为什么需要分布式锁？

想象这样一个场景：你的电商系统部署了 10 台服务器，用户抢购秒杀商品。如果没有分布式锁，可能会出现：

- **超卖问题**：100 件商品卖出了 120 件
- **重复操作**：同一笔订单被处理多次
- **数据不一致**：库存和订单对不上

分布式锁，就是为了解决这些问题而生的。

---

## 核心概念

### 什么是分布式锁？

分布式锁是一种在分布式系统中，保证同一时刻只有一个客户端能访问共享资源的机制。

```
┌─────────┐     ┌─────────┐     ┌─────────┐
│ Client1 │     │ Client2 │     │ Client3 │
└────┬────┘     └────┬────┘     └────┬────┘
     │               │               │
     └───────────────┼───────────────┘
                     ▼
              ┌─────────────┐
              │    Redis    │
              │  (Lock Key) │
              └─────────────┘
```

### 核心要求

| 要求 | 说明 |
|------|------|
| 互斥性 | 任意时刻只有一个客户端持有锁 |
| 防死锁 | 锁必须能自动释放 |
| 容错性 | Redis 部分节点宕机，锁依然有效 |
| 可重入 | 同一客户端可多次获取锁 |

---

## 实战实现

### 基础版：SET NX

```java
public boolean tryLock(String key, String value, long expireTime) {
    // SET key value NX EX expireTime
    // NX: 不存在才设置
    // EX: 设置过期时间（秒）
    return redisTemplate.opsForValue()
        .setIfAbsent(key, value, expireTime, TimeUnit.SECONDS);
}

public void unlock(String key, String value) {
    String script = 
        "if redis.call('get', KEYS[1]) == ARGV[1] then " +
        "    return redis.call('del', KEYS[1]) " +
        "else " +
        "    return 0 " +
        "end";
    redisTemplate.execute(
        new DefaultRedisScript<>(script, Long.class),
        Collections.singletonList(key),
        value
    );
}
```

⚠️ **注意**：解锁必须用 Lua 脚本，保证原子性！

### 进阶版：Redisson

```java
@Autowired
private RedissonClient redisson;

public void doSomething() {
    RLock lock = redisson.getLock("my-lock");
    try {
        // 尝试获取锁，最多等待 10 秒，锁自动释放时间 30 秒
        if (lock.tryLock(10, 30, TimeUnit.SECONDS)) {
            // 执行业务逻辑
            process();
        }
    } finally {
        // 只有当前线程持有的锁才能释放
        if (lock.isHeldByCurrentThread()) {
            lock.unlock();
        }
    }
}
```

**Redisson 优势：**
- ✅ 自动续期（看门狗机制）
- ✅ 可重入锁
- ✅ 公平锁
- ✅ 读写锁

---

## 最佳实践

### ✅ 推荐做法

| 实践 | 原因 |
|------|------|
| 设置合理的过期时间 | 避免业务执行时间超过锁过期时间 |
| 使用唯一标识作为 value | 防止误解锁 |
| 加锁和解锁要原子性 | 避免竞态条件 |
| 使用 Redisson 等成熟框架 | 避免重复造轮子 |

### ❌ 避坑指南

```java
// ❌ 错误：直接 DEL 可能删除别人的锁
redisTemplate.delete(key);

// ❌ 错误：没有设置过期时间，可能死锁
redisTemplate.opsForValue().setIfAbsent(key, value);

// ❌ 错误：过期时间太短，业务还没执行完
lock.tryLock(1, 1, TimeUnit.SECONDS);
```

---

## 总结

分布式锁是分布式系统的基础设施，核心要点：

1. **互斥性**：同一时刻只有一个客户端持有锁
2. **防死锁**：必须设置过期时间
3. **原子性**：加锁解锁操作要原子
4. **成熟方案**：生产环境推荐 Redisson

> 💡 **思考题**：如果 Redis 主节点宕机，锁会丢失吗？如何解决？（答案：Redlock 算法）

---

## 扩展阅读

- [Redis 官方文档 - Distributed Locks](https://redis.io/topics/distlock)
- [Redisson 官方文档](https://github.com/redisson/redisson/wiki)
- [Redlock 算法详解](https://martin.kleppmann.com/2016/02/08/how-to-do-distributed-locking.html)
```

---

## 📝 技术写作技巧

| 技巧 | 说明 |
|------|------|
| 开门见山 | 第一段说清楚解决什么问题 |
| 代码为主 | 代码示例比文字描述更直观 |
| 图文并茂 | 流程图、架构图帮助理解 |
| 前后呼应 | 开头提问题，结尾给答案 |
| 实战导向 | 给出可直接运行的代码 |

---

## 🔄 相关提示词

- [README 生成](readme.md)
- [API 文档](api-docs.md)
- [代码注释](comments.md)
