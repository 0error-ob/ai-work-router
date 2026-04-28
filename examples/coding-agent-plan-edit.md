# Coding Agent Plan/Edit

**任务：** 修复现有代码库中的一个 bug。bug report 清晰，仓库有测试。

**任务类型：** 编程、Agentic

## 任务结构画像

| 维度 | 取值 |
|---|---|
| Oracle 强度 | Strong — 测试、typecheck、lint |
| 视野长度 | 短多步 |
| 歧义程度 | Medium — 根因可能需要调查 |
| 上下文依赖 | Medium-high — 需要访问仓库 |
| 输出 | Patch/diff + PR 摘要 |
| 失败成本 | Medium |
| 可回滚性 | Moderate |

## 路由策略

| 阶段 | 策略 |
|---|---|
| Plan | 根因不明时用强推理；已定位则轻量规划即可 |
| Execute | 更便宜的可编程模型 |
| Verify | 测试、typecheck、lint |
| Repair | 1–2 次廉价重试；测试两次失败或范围扩大时升级 |
| Package | 廉价模型生成 PR 摘要 |

## 升级触发条件

- 测试两次失败
- 失败指向无关子系统
- 涉及文件超出预期
- Agent 提议大范围重构
- 根因仍不明确

## 不可自动化条件

- 安全敏感代码路径
- 无测试且生产风险高
- 需求不明确
- 变更需要产品判断
