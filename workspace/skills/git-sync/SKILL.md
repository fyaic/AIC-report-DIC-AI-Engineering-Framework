---
name: git-sync
description: Git 提交与分支状态检查。阶段收口提交、基线/发布打 tag、提交信息规范。运行器中立版。
---

# git-sync（运行器中立版）

## 提交流程

1. `git status` 检查——只允许本次阶段相关文件入库；无关文件/临时文件必须清理或忽略。
2. 提交信息规范：
   - 文档仓：`阶段: 内容摘要（角色）`，如 `一号仓库: v1.0.0 版本需求清单确认（PM-Agent）`
   - 代码仓：`feat|fix|test|chore(scope): 摘要（DEV-Agent）`
3. 关键节点打 tag：
   - 产品基线冻结：`baseline/vX.Y.Z`（文档仓）
   - 版本放行：`release/vX.Y.Z`（代码仓）
4. 提交后 `git log --oneline -3` 回显确认。

## 分支策略（本项目 v1.0.0）

- 主分支 `main` 承载 v1.0.0 全过程（单版本小项目，简化分支）。
- 后续版本走 `version/vX.Y.Z` 分支；冻结版本修复走 `hotfix/vX.Y.Z`。

## 禁止

1. 提交未过 doc-gatekeeper 的正式文档。
2. `git add -A` 前不检查 status。
3. force push / 改历史。
