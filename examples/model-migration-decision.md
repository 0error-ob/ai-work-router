# 模型迁移决策

**任务：** 决定是否将 coding-agent 工作流迁移到更便宜的候选模型。

**任务类型：** 推理、迁移决策

## 任务结构画像

| 维度 | 取值 |
|---|---|
| Oracle 强度 | Weak — 没有 cohort 级别的评测数据时不可信 |
| 视野长度 | Long-horizon — 影响未来大量任务 |
| 歧义程度 | High — "更好"有多个维度 |
| 上下文依赖 | High — 需要评测结果、cohort、成本数据、回滚方案 |
| 输出 | 决策建议 + 上线策略 |
| 失败成本 | High |
| 可回滚性 | Moderate — 需要提前准备 fallback |

## 路由策略

| 阶段 | 策略 |
|---|---|
| Plan | 强推理或人工主导 |
| Execute | 先只切换迁移安全的 cohort；不整体切换 |
| Verify | Cohort 级别成功率、失败模式分布、每次被接受结果的成本 |
| Repair | 保留当前模型作 fallback；weak-oracle 任务失败时升级 |
| Package | 分阶段迁移建议，含回滚条件 |

## 升级触发条件

- 候选模型在 weak-oracle cohort 上退化
- 调试循环增多
- 每次被接受结果的成本上升（尽管 token 价格更低）
- 长上下文任务质量下降
- 回滚路径不明确

## 不可自动化条件

- 只有 aggregate score，无失败分布
- 无回滚方案
- 任务 cohort 未分离
- 生产风险高
