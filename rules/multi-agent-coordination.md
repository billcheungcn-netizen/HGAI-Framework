---
id: RULE-MULTI-AGENT-COORDINATION
status: active
created: 2026-08-30
updated: 2026-08-30
source_of_truth: true
---

# 多 AI 协作与任务认领规则

## 唯一任务 ID

使用：

```text
TYPE-YYYYMMDD-HHMMSS-AGENT-XXXX
```

示例：

```text
TASK-20260830-143055-CODEX-A7F3
BUG-20260830-151210-CLAUDE-B2C8
```

`XXXX` 是随机短码。文件名必须复用完整 ID：

```text
TASK-20260830-143055-CODEX-A7F3-user-login.md
```

Commit、测试、CI、审核和交接必须引用这一稳定任务 ID。审核、交接等衍生文档可以拥有自己的同格式 ID，但必须用 `related_task` 指回主任务，不得创建无法追溯的第二套流水号。

## 开工前认领

每个写入任务开始前必须：

1. 检查 `docs/coordination/ACTIVE_TASKS.md`；
2. 检查 `tasks/active/`、`bugs/active/` 和重构任务；
3. 登记执行 AI、目标模块、目标文件、分支和开始时间；
4. 检查是否与其他 active 任务的写入范围重叠；
5. 有重叠时停止写入，由项目负责人决定合并、排序或重新划分范围。

只读调查可以并行，写入范围不得未经协调重叠。

## 任务状态头

```yaml
claimed_by: CODEX
reviewed_by: []
target_modules: []
target_files: []
claimed_at:
last_activity_at:
branch:
```

执行 AI 在重要检查点更新 `last_activity_at`。暂停或完成后释放认领并更新登记表。

## 作者与审核者

- 作者 AI 负责计划、修改、测试、文档和修订；
- 审核 AI 默认只读，检查用户需求、模块、架构、测试、Git 和安全；
- 同一任务的作者与审核者默认不得是同一 AI 身份；
- 审核意见写入独立 REVIEW 文档；
- 审核 AI 不得直接改写作者工作区，除非完成明确的写入权交接；
- 原作者根据审核意见修订，或项目负责人将任务正式移交；
- 严格模式在可用时优先安排不同 AI 交叉审核。

## 工作区和分支

多个 AI 同时工作时优先使用独立分支或独立工作区。不得依靠口头约定让两个 AI 同时修改同一未隔离工作树。

## 初始化交叉审核

首次生成 `AGENTS.md`、模块地图、术语表、测试现状和规则库后，应由第二个 AI 对照真实代码只读复核。初始化审核通过前，不进入高风险功能开发。
