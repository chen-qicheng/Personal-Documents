# Git 命令速查手册

> 常用 Git 命令快速参考，涵盖日常开发中的高频操作。

## 初始化仓库


| 命令                   | 说明               |
| ---------------------- | ------------------ |
| `git init`             | 初始化本地仓库     |
| `git clone <仓库地址>` | 克隆远程仓库到本地 |

```bash
# 示例
git init
git clone git@192.168.122.20:pdd/HWAMR.git
```

---

## 基本操作

### 添加与提交


| 命令                             | 说明                                       |
| -------------------------------- | ------------------------------------------ |
| `git add <文件名>`               | 添加指定文件到暂存区（多个文件用空格分隔） |
| `git add .`                      | 添加所有修改到暂存区                       |
| `git add -p <文件名>`            | 拆分提交（交互式选择代码块）               |
| `git commit -m "注释"`           | 提交暂存区的更改                           |
| `git commit --amend -m "新注释"` | 修改最后一次提交的注释                     |

### 推送与拉取


| 命令                       | 说明               |
| -------------------------- | ------------------ |
| `git pull origin <分支名>` | 拉取指定分支的更新 |
| `git push origin <分支名>` | 推送到指定分支     |

```bash
git pull origin WFCT-960-V1.1
git push origin WFCT-960-V1.1
```

---

## 分支管理

> 分支操作主要使用 `git branch` 和 `git switch` 两个命令完成。


| 命令                                                        | 说明                       |
| ----------------------------------------------------------- | -------------------------- |
| `git branch`                                                | 查看所有分支及当前所在分支 |
| `git branch <分支名>`                                       | 创建新分支                 |
| `git branch -d <分支名>`                                    | 删除分支（已合并）         |
| `git branch -D <分支名>`                                    | 强制删除分支               |
| `git switch <分支名>`                                       | 切换到指定分支             |
| `git switch -c <分支名>`                                    | 创建并切换到新分支         |
| `git switch -c <分支名> <远程主机名> <远程分支>`            | 从远程克隆分支并切换       |
| `git merge <分支名>`                                        | 合并指定分支到当前分支     |
| `git merge --no-ff -m "注释" <分支名>`                      | 禁用 Fast forward 合并     |
| `git branch --set-upstream-to=origin/<远程分支> <本地分支>` | 建立追踪关系               |

---

## 标签管理


| 命令                                  | 说明                             |
| ------------------------------------- | -------------------------------- |
| `git tag`                             | 查看所有标签                     |
| `git tag <标签名>`                    | 为当前 commit 打标签             |
| `git tag <标签名> <commit id>`        | 为指定 commit 打标签             |
| `git tag -a <标签名> -m "注释"`       | 创建带注释的标签                 |
| `git tag -d <标签名>`                 | 删除本地标签                     |
| `git push origin <标签名>`            | 推送指定标签到远程               |
| `git push origin --tags`              | 推送所有标签到远程               |
| `git push origin :refs/tags/<标签名>` | 删除远程标签（需先删除本地标签） |

---

## 撤销修改

> ⚠️ 官方不再推荐使用 `git checkout`，建议使用 `git restore`。


| 命令                            | 说明                                 |
| ------------------------------- | ------------------------------------ |
| `git restore <文件名>`          | 将工作区的文件从暂存区恢复           |
| `git restore --staged <文件名>` | 将暂存区的文件从分支恢复（取消 add） |

### 使用场景

1. **已修改但未 add**：直接使用 `git restore <文件名>`
2. **已 add 但未 commit**：先执行 `git restore --staged <文件名>`，再执行 `git restore <文件名>`

---

## 版本回退


| 命令                        | 说明                             |
| --------------------------- | -------------------------------- |
| `git reset --hard HEAD^`    | 回退到上一个版本                 |
| `git reset --hard HEAD^^`   | 回退到上两个版本                 |
| `git reset --hard HEAD~100` | 回退到前 100 个版本              |
| `git reset <commit id>`     | 回退到指定 commit（id 无需输完） |

> 使用 `git log` 查看 commit 历史信息。

---

## Stash 暂存


| 命令                              | 说明                       |
| --------------------------------- | -------------------------- |
| `git stash`                       | 暂存当前修改（默认无描述） |
| `git stash save "描述信息"`       | 暂存并添加描述             |
| `git stash list`                  | 列出所有暂存               |
| `git stash pop`                   | 恢复最近的一次暂存并移除   |
| `git stash apply stash@{index}`   | 恢复指定的暂存             |
| `git stash show -p stash@{index}` | 查看指定暂存的内容         |
| `git stash drop stash@{index}`    | 删除指定的暂存             |
| `git stash clear`                 | 清除所有暂存               |

---

## Cherry-pick


| 命令                          | 说明                         |
| ----------------------------- | ---------------------------- |
| `git cherry-pick <commit id>` | 将指定 commit 复制到当前分支 |

---

## 远程仓库


| 命令                                 | 说明             |
| ------------------------------------ | ---------------- |
| `git remote -v`                      | 查看远程仓库地址 |
| `git remote set-url origin <新地址>` | 修改远程仓库地址 |

```bash
git remote set-url origin git@github.com:chen-qicheng/LearnCpp.git
```

---

## 拆分提交

使用 `git add -p` 可以交互式地选择代码块进行提交：

```bash
git add -p <文件名>
```

### 交互选项


| 按键 | 说明                       |
| ---- | -------------------------- |
| `y`  | 暂存此区块                 |
| `n`  | 不暂存此区块               |
| `q`  | 退出，不暂存剩余区块       |
| `a`  | 暂存此块及后续所有区块     |
| `d`  | 不暂存此块及后续所有区块   |
| `g`  | 选择并跳转至指定区块       |
| `/`  | 搜索匹配正则的区块         |
| `j`  | 跳过，转至下一个未决定区块 |
| `J`  | 跳过，转至下一个区块       |
| `k`  | 跳过，转至上一个未决定区块 |
| `K`  | 跳过，转至上一个区块       |
| `s`  | 将当前区块分割成多个小区块 |
| `e`  | 手动编辑当前区块           |
| `?`  | 输出帮助                   |

---

## 忽略文件

### .gitignore

- 在项目根目录创建 `.gitignore` 文件
- Git 会自动忽略符合规则的文件
- **`.gitignore` 只能忽略未被追踪的文件**
- 需要将 `.gitignore` 文件本身推送到远程仓库
- 使用 `git add -f <文件名>` 可强制添加被忽略的文件

### 示例

```gitignore
# 忽略文件夹
/.vscode
/build

# 忽略文件
*.log
*.tmp
```

### 其他命令


| 命令                       | 说明                   |
| -------------------------- | ---------------------- |
| `git rm --cached <文件名>` | 停止追踪已提交的文件   |
| `git diff --staged`        | 查看暂存区与分支的差异 |

---

## 常见问题

### Windows 文件名大小写

Git 在 Windows 下**默认不区分文件名大小写**。

---

## Git 配置

### SSH 密钥

```bash
# 生成 SSH 密钥
ssh-keygen

# 测试 GitHub 连接
ssh -T git@github.com
```

### Tab 自动补全

如果 Tab 键无法自动补全 Git 命令：

```bash
source /usr/share/bash-completion/completions/git
# 或
source /etc/bash_completion.d/git
```

### 翻墙软件导致无法连接 GitHub

编辑或新建 `~/.ssh/config` 文件（Windows）：

```config
Host github.com
    User git
    ProxyCommand connect -H 127.0.0.1:7890 %h %p
    Hostname ssh.github.com
    Port 443
```

---

## 参考链接

- [GitHub 使用指导 - 菜鸟教程](https://www.runoob.com/w3cnote/git-guide.html)
- [Git 远程仓库 - 菜鸟教程](https://www.runoob.com/git/git-remote-repo.html)

---

*最后更新：2026年3月*
