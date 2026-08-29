# Claude Code 项目入口

开始任何任务前：

1. 完整阅读项目根目录的 `AGENTS.md`；
2. 阅读 `docs/rules/INDEX.md` 及当前任务适用的规则；
3. 检查 `docs/coordination/ACTIVE_TASKS.md`，生成唯一任务 ID 并确认写入范围没有冲突；
4. 按 Token 定位阶梯从文件或模块级开始调查；
5. 根据任务风险选择 `TASK_LITE.md`、`TASK.md` 或 `BUG.md`；
6. 技术过程写入内部文档，面向项目负责人的反馈遵守 `user-facing-communication.md`；
7. 不得绕过 Git、自动化测试、统一验证入口、CI、文档防腐、依赖与密钥规则；
8. 作为审核 AI 时默认只读，把结论写入 REVIEW 文档，不直接修改作者工作区。

如果本文件与权威规则冲突，以 `docs/rules/` 和项目 `AGENTS.md` 为准。
