# 敏货看台 测试 Skill 链（运行器中立版）

本目录是把 `tool-repo/08_AI工作站/02_Skill_Agent与执行/Claude|Codex/` 的 16 个 Skill
蒸馏后的运行器中立版本，供本测试中任何 AI 运行器（ZCode/Claude/Codex）的子代理直接执行。

蒸馏原则（也是一条测试发现的原版断点）：
原版 Skill 与 Claude/Codex 插件机制耦合（AskUserQuestion、bootstrap、install receipt），
在其他运行器上不可直接执行；本版把「判断逻辑+强制规则+输出契约」抽为纯文本协议。

## 调用链

```text
warehouse-router → 阶段 Skill（od-demand-analyzer / project-governance / req-analyze /
prd / product-baseline / tech-solution / qa-execute）→ doc-gatekeeper → git-sync
```

## Skill 清单

| Skill | 文件 | 对应仓库 | 执行角色 |
| --- | --- | --- | --- |
| warehouse-router | [warehouse-router/SKILL.md](warehouse-router/SKILL.md) | 全仓 | 任意（进入前） |
| od-demand-analyzer | [od-demand-analyzer/SKILL.md](od-demand-analyzer/SKILL.md) | 00_OD工作区 | OD |
| project-governance | [project-governance/SKILL.md](project-governance/SKILL.md) | 01_零号仓库 | OD+PM |
| req-analyze | [req-analyze/SKILL.md](req-analyze/SKILL.md) | 02_一号仓库 | PM |
| prd | [prd/SKILL.md](prd/SKILL.md) | 03_二号仓库 | PM |
| product-baseline | [product-baseline/SKILL.md](product-baseline/SKILL.md) | 03_二号仓库 | PM+PD |
| tech-solution | [tech-solution/SKILL.md](tech-solution/SKILL.md) | 04_三号仓库 | DEV |
| qa-execute | [qa-execute/SKILL.md](qa-execute/SKILL.md) | 05_四号仓库 | QA |
| doc-gatekeeper | [doc-gatekeeper/SKILL.md](doc-gatekeeper/SKILL.md) | 全仓 | 任意（落库前） |
| git-sync | [git-sync/SKILL.md](git-sync/SKILL.md) | 全仓 | 任意（提交前） |
