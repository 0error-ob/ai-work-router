# AI Work Router

Where is intelligence actually needed in this workflow?

Route by workflow phase — not by prompt. Decide where to use strong reasoning, where cheaper execution is safe, what verifier to use, and when to stop.

Markdown-only: a prompt, a template, and worked examples.

## How to use it

### 1. Use the prompt

Copy `prompts/create-routing-card.md` into your preferred LLM and paste your task or workflow.

Fast first-pass routing card.

### 2. Use the template

Fill out `templates/ai-work-routing-card.md` manually.

Think through oracle strength, ambiguity, failure cost, workflow phases, and escalation yourself.

### 3. Ask for a card

Send a task or workflow to someone familiar with the framework. Receive a completed AI Work Routing Card.

Good for high-cost, ambiguous, agentic, or model-migration tasks.

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
