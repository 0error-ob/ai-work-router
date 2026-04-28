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

**Let AI fill the template** — expand below, copy the prompt, send to your LLM. Output is a filled structured card you can review field by field.

<details>
<summary>Expand prompt (AI fills template format)</summary>

Fill in this AI Work Routing Card for me. Analyze my task and complete each field.

**My task:**

[Describe the task here]

---

**Task type**

Answer / Rewrite / Extract / Classify / Generate / Reason / Code / Agentic / Research / Data analysis / Other

**Task-structure profile**

| Dimension | Value | Notes |
|---|---|---|
| Oracle strength | | |
| Horizon | | |
| Ambiguity load | | |
| Context dependency | | |
| Output constraint | | |
| Failure cost | | |
| Reversibility | | |

**Routing policy**

| Phase | Model class / tool |
|---|---|
| Plan | |
| Execute | |
| Verify | |
| Repair | |
| Finalize | |

Model classes: strong reasoning · cheaper execution · coding-capable · long-context · structured-output-stable · deterministic verifier · human review

**Escalation triggers**

**Do-not-automate conditions**

</details>

**Ask for a card** — expand below, copy the request, send it to someone familiar with the framework.

<details>
<summary>Expand request template</summary>

I have a task and need an AI Work Routing Card — help me figure out how to split it across model classes and workflow phases.

**Task:**

[Describe the task here]

**Context:**
- Cost constraints:
- Failure consequences:
- Verification available:
- Current workflow:

Framework reference: https://github.com/0error-ob/ai-work-router

</details>

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