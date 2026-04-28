[中文](README.md)

# AI Work Router

Where is intelligence actually needed in this workflow?

Route by workflow phase — not by prompt. Decide where to use strong reasoning, where cheaper execution is safe, what verifier to use, and when to stop.

Markdown-only: a prompt, a template, and worked examples.

## How to use it

Pick whichever fits:

**Use the prompt** — copy `prompts/create-routing-card.md` into your preferred LLM and paste your task. Fast first-pass.

**Use the template** — fill out `templates/ai-work-routing-card.md` yourself. Good when you want to think through oracle strength, ambiguity, and failure cost directly.

**Ask for a card** — send a task or workflow to someone familiar with the framework. Good for high-cost, ambiguous, or model-migration tasks.

## Example

Task: modify a small function according to an explicit plan and run tests.

| Phase | Policy |
|---|---|
| Plan | already provided — skip |
| Execute | cheaper coding-capable model |
| Verify | run tests / typecheck |
| Repair | one cheap retry |
| Escalate | use stronger reasoning if tests fail twice or root cause is unclear |

## Phases

Intake → Planning → Search → Execute → Verify → Repair → Package

## More examples

`examples/coding-agent-plan-edit.md` · `examples/batch-json-extraction.md` · `examples/model-migration-decision.md`

## Roadmap

Future versions may explore interactive card generation, a local CLI, and a BYOK app. Only after real usage signals.
