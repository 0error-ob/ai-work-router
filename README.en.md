[中文](README.md)

# AI Work Router

Where is intelligence actually needed in this workflow?

Route by workflow phase — not by prompt. Decide where to use strong reasoning, where cheaper execution is safe, what verifier to use, and when to stop.

## How to use it

Copy the prompt below, paste into your LLM, and add your task.

---

Analyze an AI work task and produce an executable workflow routing strategy.

Your goal is not to recommend a "single best model." Instead, judge:

- Which phases warrant strong reasoning
- Which phases can use cheaper execution
- Which phases should prioritize deterministic verifiers
- When to escalate, stop, or require human review
- Whether this task is suitable for automation

**Task:**

[Paste task description here]

**Optional context:** Cost sensitivity / Failure cost / Verification available / Tools available / Context size / Involves code or data

**First, complete this analysis internally (do not output):**

- Task-structure profile: oracle strength / horizon / ambiguity / context dependency / output constraint / failure cost / reversibility / cost sensitivity
- Workflow decomposition: intake / plan / search / execute / verify / repair / package — for each phase, its goal, recommended routing, reasoning level
- Escalation triggers and stop / do-not-automate conditions

**Then output only the Quick Routing block:**

- Intake: [model class] · [reasoning level] · [one-line action]
- Plan: ...
- Search / Context: ...
- Execute: ...
- Verify: ...
- Repair: ...
- Package: ...

Keep each line terse. Model classes: strong reasoning · cheaper execution · coding-capable · long-context · structured-output-stable · deterministic verifier · human review. Do not use specific model names. When a deterministic verifier is available, do not default to LLM judgment. When a task can be split into plan / execute / verify, do not hand it to a single model.

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
