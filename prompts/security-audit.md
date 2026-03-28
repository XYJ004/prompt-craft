# 🛡️ 安全审计提示词

## 🎯 适用场景

- 代码安全检查
- 漏洞扫描
- 安全最佳实践
- 合规性检查

---

## 💡 综合安全审计

```
你是网络安全专家，请对以下代码进行全面的安全审计。

## 代码信息
- 语言/框架：[如 PHP / Laravel]
- 部署环境：[如 公网 / 内网]
- 敏感数据：[如 用户密码、支付信息]

## 待审计代码
```
[粘贴代码]
```

## 审计维度

### 1. 注入漏洞
- SQL 注入
- 命令注入
- XSS（跨站脚本）
- LDAP 注入

### 2. 认证授权
- 密码存储方式
- Session 管理
- 权限检查
- 越权访问

### 3. 数据安全
- 敏感数据加密
- 日志脱敏
- 传输安全

### 4. 其他安全
- CSRF 防护
- 文件上传
- 错误信息泄露
- 依赖安全

## 输出格式

### 🛑 高危漏洞
| 漏洞类型 | 位置 | 风险等级 | 修复方案 |
|----------|------|----------|----------|
| SQL注入 | login.php:15 | 高 | 参数化查询 |

### ⚠️ 中危漏洞
| 漏洞类型 | 位置 | 风险等级 | 修复方案 |
|----------|------|----------|----------|

### 📋 安全建议
[一般性安全建议]
```

---

## 💡 SQL 注入检测

```
检查以下代码是否存在 SQL 注入漏洞：

```[语言]
[代码]
```

检查点：
1. 字符串拼接 SQL
2. 用户输入直接入 SQL
3. 参数化查询使用
4. ORM 安全使用

请列出所有可疑位置并给出修复代码。
```

---

## 💡 XSS 检测

```
检查以下前端代码是否存在 XSS 漏洞：

```javascript
[代码]
```

检查点：
1. innerHTML 使用
2. 用户输入渲染
3. URL 参数使用
4. 存储型 XSS

请列出所有可疑位置并给出修复方案。
```

---

## 🌟 效果展示

**输入：**
```php
function login($username, $password) {
    $query = "SELECT * FROM users WHERE username = '$username' AND password = '$password'";
    $result = mysqli_query($conn, $query);
    return mysqli_fetch_assoc($result);
}
```

**输出：**
```
### 🛑 高危漏洞

| 漏洞类型 | 位置 | 风险等级 | 修复方案 |
|----------|------|----------|----------|
| SQL 注入 | 第2行 | 🔴 高 | 使用参数化查询 |
| 明文密码 | 第2行 | 🔴 高 | 使用 bcrypt 加密 |

### 🔧 修复代码

```php
function login($username, $password) {
    // 参数化查询
    $stmt = $conn->prepare("SELECT * FROM users WHERE username = ?");
    $stmt->bind_param("s", $username);
    $stmt->execute();
    $result = $stmt->get_result();
    $user = $result->fetch_assoc();
    
    // 密码验证
    if ($user && password_verify($password, $user['password'])) {
        return $user;
    }
    return null;
}
```

### 📋 安全建议

1. 所有用户输入使用参数化查询
2. 密码使用 `password_hash()` 加密存储
3. 添加登录失败次数限制
4. 记录登录日志
```

---

## 📝 OWASP Top 10 检查清单

| 漏洞 | 检查项 |
|------|--------|
| 注入 | 参数化查询、输入验证 |
| 失效认证 | 密码策略、Session 管理 |
| 敏感数据泄露 | 加密传输、存储加密 |
| XML 外部实体 | 禁用外部实体 |
| 访问控制失效 | 权限检查、最小权限 |
| 安全配置错误 | 关闭调试、安全头 |
| XSS | 输出编码、CSP |
| 不安全的反序列化 | 白名单验证 |
| 组件漏洞 | 依赖更新、漏洞扫描 |
| 日志不足 | 审计日志、监控告警 |

---

## 🔄 相关提示词

- [代码审查](code-review.md)
- [Bug 调试](debug.md)
- [性能优化](performance.md)
