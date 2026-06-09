# Git Merge vs Rebase 图解演示

> ⚠️ 这是一个**演示仓库**，用于直观对比 Git Merge 和 Rebase 的历史图差异。
> 代码文件（login.js、register.js、dashboard.js、profile.js）均为模拟数据，无实际功能。

## 仓库结构

| 分支 | 内容 |
|------|------|
| [`merge`](https://github.com/Cnjszzw/git-merge-vs-rebase-demo/tree/merge) | 模拟多人协作使用 `git merge`（默认 pull）后的 commit 历史 |
| [`rebase`](https://github.com/Cnjszzw/git-merge-vs-rebase-demo/tree/rebase) | 同样场景使用 `git pull --rebase` 后的 commit 历史 |

## 直观对比

**Network Graph 看最清楚：**
https://github.com/Cnjszzw/git-merge-vs-rebase-demo/network

- 切换到 `merge` 分支 → 分支分叉再汇合的网状结构
- 切换到 `rebase` 分支 → 一条直线，无分叉

## 场景说明

模拟两个开发者（用户A 和 用户B）协作：

1. 用户A clone → 写代码 → commit → push 到远端
2. 用户B clone → 写代码 → commit 本地 → 尝试 push 时发现 A 已推送
3. B 需要同步：
   - `merge` 分支：B 用 `git pull`（默认 merge）→ 产生一个 Merge commit
   - `rebase` 分支：B 用 `git pull --rebase` → commit 被搬到 A 后面

## 本地查看

```bash
git clone https://github.com/Cnjszzw/git-merge-vs-rebase-demo.git
git log --oneline --graph merge
git log --oneline --graph rebase
```

## 讲解页面

本仓库搭配静态 HTML 讲解页面使用，打开 [`diff.html`](diff.html) 即可在浏览器中查看基于 WVP 真实提交记录绘制的 JetBrains 风格 Git 图。
