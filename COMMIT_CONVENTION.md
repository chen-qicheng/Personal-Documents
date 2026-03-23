# 提交信息规范 (Angular Commit Convention)

本项目遵循 [Angular Commit Message Conventions](https://github.com/angular/angular/blob/main/CONTRIBUTING.md#-commit-message-format) 规范。

---

## 格式

```
<type>(<scope>): <subject>
<BLANK LINE>
<body>
<BLANK LINE>
<footer>
```

### 简化格式（最常用）

```
<type>(<scope>): <subject>
```

---

## 类型 (Type)

| 类型 | 说明 | 示例 |
|------|------|------|
| **feat** | 新功能 | `feat: 添加用户登录功能` |
| **fix** | 修复 bug | `fix: 修复登录验证失败问题` |
| **docs** | 文档更新 | `docs: 更新 README 安装说明` |
| **style** | 代码格式（不影响功能） | `style: 统一代码缩进格式` |
| **refactor** | 代码重构 | `refactor: 重构用户认证逻辑` |
| **perf** | 性能优化 | `perf: 优化数据库查询速度` |
| **test** | 测试相关 | `test: 添加用户模块单元测试` |
| **chore** | 构建/工具/依赖更新 | `chore: 升级依赖包版本` |
| **ci** | CI/CD 配置 | `ci: 添加自动化部署脚本` |
| **build** | 构建系统 | `build: 配置 webpack 打包` |
| **revert** | 回滚提交 | `revert: 回滚 feat: 添加实验性功能` |

---

## 作用域 (Scope)

可选，用于指定修改范围：

```
feat(auth): 添加 OAuth 登录
fix(api): 修复接口响应超时问题
docs(readme): 更新项目说明
```

常用作用域示例：
- `api` - 接口相关
- `ui` - 界面相关
- `auth` - 认证相关
- `config` - 配置相关
- `docs` - 文档相关

---

## 主题 (Subject)

- 简短描述，不超过 100 字符
- 使用第一人称现在时（"change" 而非 "changed" 或 "changes"）
- 首字母小写
- 末尾不加句号

✅ 正确示例：
```
feat: 添加用户注册功能
fix: 修复页面加载缓慢问题
docs: 更新 API 文档
```

❌ 错误示例：
```
Added user registration feature      # 使用了过去时
feat: Added user registration        # 首字母大写
feat: 添加用户注册功能。              # 末尾有句号
feat                                   # 缺少主题描述
```

---

## 正文 (Body)

可选，用于详细说明修改内容：

```
feat(auth): 添加用户注册功能

- 实现邮箱验证机制
- 添加密码强度检测
- 集成短信验证码服务

Closes #123
```

---

## 页脚 (Footer)

可选，用于引用 issue 或破坏性变更说明：

```
BREAKING CHANGE: 用户认证接口参数已变更

Closes #456
Refs #789
```

---

## 完整示例

```
feat(auth): 添加用户登录功能

实现基于 JWT 的用户认证系统：
- 添加登录/登出接口
- 实现 Token 刷新机制
- 添加登录状态持久化

Closes #42
```

---

## 提交钩子

本项目已配置 `commit-msg` 钩子，会自动验证提交信息格式。

如果提交信息不符合规范，将收到错误提示并阻止提交。

---

## 参考

- [Angular Commit Message Guidelines](https://github.com/angular/angular/blob/main/CONTRIBUTING.md#-commit-message-format)
- [Conventional Commits](https://www.conventionalcommits.org/)
