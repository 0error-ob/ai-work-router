[中文](README.md)

# AI Work Router

Where is intelligence actually needed in this workflow?

Route by workflow phase — not by prompt. Decide where to use strong reasoning, where cheaper execution is safe, what verifier to use, and when to stop.

## How to use it

Copy the prompt below, paste into your LLM, and add your task.

---

Analyze this AI work task and give an executable workflow routing recommendation.

**Task:**

[Paste task description here]

**Optional context:** Cost sensitivity / Failure cost / Verification available / Tools available / Context size

**Output:** Give a routing recommendation in 3–7 lines using this format:

- Intake:
- Plan:
- Search / Context:
- Execute:
- Verify:
- Repair:
- Package:

Each line should state the model class, reasoning level, and what specifically happens. Model classes: strong reasoning · cheaper execution · coding-capable · long-context · structured-output-stable · deterministic verifier · human review. Do not use specific model names. When a deterministic verifier is available, use it before LLM judgment.

---

For a full task-structure analysis (9 sections with escalation triggers and Agent Instruction) → [AI Work Routing Card](routing-card.en.md)

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
