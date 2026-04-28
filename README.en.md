[中文](README.md)

# AI Work Router

Where is intelligence actually needed in this workflow?

Route by workflow phase — not by prompt. Decide where to use strong reasoning, where cheaper execution is safe, what verifier to use, and when to stop.

Markdown-only: a prompt, a template, and worked examples.

## How to use it

Pick whichever fits:

**Use the prompt** — expand below, copy the prompt, paste into your preferred LLM, then add your task.

<details>
<summary>Expand prompt</summary>

Analyze the task structure and produce a workflow routing policy. Do not recommend a single best model.

**Task:**

[Paste your task here]

**Optional context:** Cost sensitivity / Failure cost / Verification available / Tools available / Context size

**Output:** Produce a complete AI Work Routing Card covering task · task type · task-structure profile (oracle strength, horizon, ambiguity, context dependency, output constraint, failure cost, reversibility) · workflow decomposition (intake → plan → search → execute → verify → repair → package) · routing policy by phase · escalation triggers · do-not-automate conditions · rationale

Use model classes, not model names: strong reasoning · cheaper execution · coding-capable · long-context · structured-output-stable · deterministic verifier · human review. Prefer deterministic verification. Be specific about escalation triggers and stop conditions.

</details>

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