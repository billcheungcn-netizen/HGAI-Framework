---
id: RULE-DOCUMENT-GOVERNANCE
status: active
created: 2026-08-29
updated: 2026-08-29
source_of_truth: true
---

# 文档防腐与唯一权威来源规则

## SSOT

- 同一事实只在一个权威文档完整描述；
- 其他文档引用权威文档，不复制整段内容；
- 代码现实与文档冲突时必须调查，不自动认定任何一方正确；
- 任务结束时同步更新受影响的权威文档。

## 状态头

过程文档必须包含：

```yaml
---
id:
status: draft | active | completed | superseded | archived
created:
updated:
source_of_truth: true | false
supersedes:
superseded_by:
related_commits:
---
```

## 索引分层

- `AGENTS.md`：只保留当前有效规则、当前任务、当前架构入口和少量关键历史；
- `docs/INDEX.md`：登记所有 active、completed、superseded 和 archived 文档；
- `docs/archive/`：保存不再参与日常上下文的历史材料；
- 调查历史问题时才读取归档。

## 裁剪触发

项目在 `AGENTS.md` 中配置裁剪周期或数量阈值。触发后：

1. 找出已完成且不再影响当前工作的任务；
2. 找出被替代、重复或过期文档；
3. 更新状态和替代关系；
4. 从 `AGENTS.md` 移除，保留在全量登记表；
5. 检查主索引 Token 和重复内容是否下降。

## 文件命名

```text
YYYYMMDD-HHMM-类型-简述.md
```

稳定 ID 用于文档、Commit、测试和规则之间的关联，文件名用于自然时间排序。

