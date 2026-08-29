---
id: RULE-INDEX
status: active
created: 2026-08-29
updated: 2026-08-29
source_of_truth: true
---

# 常驻规则索引

> 初始化项目时，将本目录复制为项目的 `docs/rules/`。这里是规则的唯一权威来源。

| 规则 | 适用场景 | 必须阅读 |
|---|---|---|
| `user-facing-communication.md` | 需求理解、计划审核、完成反馈 | 所有任务 |
| `git-workflow.md` | 修改代码、提交、回退、重构 | 所有代码任务 |
| `testing.md` | 功能、Bug、重构和验证 | 所有行为变化 |
| `document-governance.md` | 创建、更新、替代和归档文档 | 所有任务结束时 |
| `dependencies-and-secrets.md` | 新依赖、配置、凭据和日志 | 涉及依赖或配置时 |
| `architecture-boundaries.md` | 新功能、跨模块修改和重构 | 所有代码任务 |
| `bug-diagnosis.md` | 故障调查和 Bug 修复 | 所有 Bug |

## 规则沉淀流程

```text
踩坑或 AI 跑偏
→ 判断是否可能再次发生
→ 使用 RULE.md 起草规则
→ 人审核适用范围和副作用
→ 加入本目录
→ 更新本索引和工具入口
→ 在后续代表性任务中验证规则有效
```

## 防止规则膨胀

- 一条规则只解决一种可重复问题；
- 已有规则能覆盖时更新原规则，不新建近义规则；
- 规则必须有触发条件、适用范围、必须动作、禁止动作和验证方法；
- 过时规则标记 `superseded`，并指向替代规则；
- 工具入口只引用规则，不复制完整内容；
- 定期合并重复规则并删除无效示例。

