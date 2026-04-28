[中文](README.md)

# AI Work Router

Where is intelligence actually needed in this workflow?

Route by workflow phase — not by prompt. Decide where to use strong reasoning, where cheaper execution is safe, what verifier to use, and when to stop.

## How to use it

Copy the prompt below, paste into your LLM, and add your task.

---

Analyze an AI work task and produce an AI work routing recommendation that a regular user can follow.

Your goal is not to recommend a "single best model." Instead, judge:

- Which steps deserve a strong model thinking carefully
- Which steps can be handed to a cheap/fast model
- Which steps should use tools, tests, tables, or rules to check
- When to escalate to a stronger model
- When automation should stop and let a human decide

## Task

[Paste task description here]

## Optional context

- Cost sensitivity:
- Failure cost:
- Verification available:
- Tools available:
- Context size:
- Involves code / data / files / external pages:
- Current pain points:

## Internal analysis (do this silently)

Complete the following analysis internally — do not output it as a list of jargon:

- Task structure: verification difficulty, task length, ambiguity, context dependency, output constraint, failure cost, reversibility, cost sensitivity
- Workflow decomposition: understand task → plan → search/gather → execute → check → fix → deliver
- Which steps need strong reasoning, which can use cheap execution, which need deterministic checks
- Escalation triggers and stop conditions

## Output requirements

Output only a concise **AI Work Routing**.

Do not output the full analysis report.
Do not pile up jargon.
Do not use specific model names.
Do not say "best model."
Each step must tell the user: what to do next, what kind of model/tool to use, why.

## Output format

# AI Work Routing

## One-line strategy

State in one sentence how this task should split AI work.

## Recommended steps

Output by step. Each step uses this format:

### 1. [Step name]

**What to do:**
One sentence describing what this stage accomplishes.

**What to use:**
Choose one or more from below, explained in natural language:

- A strong model planning carefully
- A cheap/fast model executing
- A long-context model reading large material
- A structured-output model organizing into a table / JSON / checklist
- A tool / test / rule check
- Human judgment

**Why:**
One sentence on why this allocation makes sense.

## Check points

List the 3–5 most important things to check for this task.
Prefer tools, tables, tests, rules, or calculation over asking another LLM to judge by feel.

## When to escalate

List specific escalation conditions.
Examples: conflicting information, two consecutive failures, budget exceeded, tests failing, requirements becoming unclear, risk increasing.

## When to stop automation

List cases requiring human judgment.
Examples: high-risk decisions, real payments, legal / visa / medical / financial risk, information that cannot be verified, unclear user preferences.

## Final deliverable

State what form the final output should take so the user can use it directly.

---

Want the engineer version (full 9 sections, terminology, Agent Instruction)? → [AI Work Routing Card](routing-card.en.md)

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
