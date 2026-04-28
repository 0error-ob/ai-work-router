[English](README.en.md)

# AI Work Router

这个工作流里，哪些地方真正需要智能？

按工作流阶段路由，而不是按 prompt 路由。决定哪里用强推理，哪里用更便宜的执行，用什么验证器，以及何时停止。

纯 Markdown：一个 prompt、一个模板、几个示例。

## 如何使用

选一种适合的方式：

**用 prompt** — 把 `prompts/create-routing-card.md` 复制到你常用的 LLM，粘贴你的任务。快速得到第一版 routing card。

**用模板** — 自己填写 `templates/ai-work-routing-card.md`。适合想亲自梳理 oracle 强度、歧义度、失败成本的情况。

**请人出卡** — 把任务或工作流发给熟悉这套框架的人，让他们生成一张完整的 AI Work Routing Card。适合高成本、高歧义、agentic 或模型迁移类任务。

## 示例

任务：按照明确的计划修改一个小函数，并运行测试。

| 阶段 | 策略 |
|---|---|
| Plan | 已有计划 — 跳过 |
| Execute | 更便宜的可编程模型 |
| Verify | 运行测试 / typecheck |
| Repair | 一次廉价重试 |
| Escalate | 若测试两次失败或根因不明，升级到强推理模型 |

## 工作流阶段

Intake → Planning → Search → Execute → Verify → Repair → Package

## 更多示例

`examples/coding-agent-plan-edit.md` · `examples/batch-json-extraction.md` · `examples/model-migration-decision.md`

## Roadmap

未来可能探索：交互式卡片生成、本地 CLI、BYOK 应用。仅在有真实用户信号后才会推进。
