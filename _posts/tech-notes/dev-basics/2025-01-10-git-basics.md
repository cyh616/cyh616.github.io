---
title: Git 基础操作笔记
date: 2025-01-10 22:04:00 +0800
categories: [技术笔记, 开发基础]
tags: [git, 版本控制]
author: CYH
toc: true
---

## Git 基础操作笔记

记录 Git 常用命令和工作流程，方便日常查阅。

### 1. 配置 Git

```bash
# 设置用户信息
git config --global user.name "你的名字"
git config --global user.email "你的邮箱"
# 查看配置
git config --list
```

### 2. 仓库操作

```bash
# 初始化仓库
git init
# 克隆仓库
git clone <仓库地址>
# 查看状态
git status
```

### 3. 文件操作

```bash
# 添加文件到暂存区
git add <文件名>
git add .  # 添加所有文件

# 提交更改
git commit -m "提交说明"

# 查看提交历史
git log
```

### 4. 分支操作

```bash
# 查看分支
git branch

# 创建分支
git branch <分支名>

# 切换分支
git checkout <分支名>
# 或使用新命令
git switch <分支名>

# 合并分支
git merge <分支名>
```

### 5. 远程操作

```bash
# 添加远程仓库
git remote add origin <仓库地址>

# 推送到远程
git push origin <分支名>

# 拉取更新
git pull origin <分支名>
```

### 6. 常用工作流程

1. 更新代码
```bash
git pull origin main
```

2. 创建功能分支
```bash
git checkout -b feature/new-feature
```

3. 提交更改
```bash
git add .
git commit -m "feat: 添加新功能"
```

4. 推送更改
```bash
git push origin feature/new-feature
```

### 7. 提交规范

- feat: 新功能
- fix: 修复问题
- docs: 文档更新
- style: 代码格式
- refactor: 重构
- test: 测试
- chore: 构建过程或辅助工具的变动

### 8. 常见问题处理

```bash
# 撤销未提交的更改
git checkout -- <文件名>

# 撤销最后一次提交
git reset --soft HEAD^

# 强制推送
git push -f origin <分支名>  # 谨慎使用
```

## 参考资料

- [Git 官方文档](https://git-scm.com/doc)
- [GitHub Git 教程](https://docs.github.com/cn/get-started/getting-started-with-git)

> 注意：本笔记仅供个人学习参考，建议结合官方文档使用。