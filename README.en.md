[中文](README.md)

# AI Work Router

Where is intelligence actually needed in this workflow?

Route by workflow phase — not by prompt. Decide where to use strong reasoning, where cheaper execution is safe, what verifier to use, and when to stop.

## How to use it

Copy the prompt below, paste into your LLM, and add your task.

---

```
Analyze an AI work task and produce an AI work routing recommendation that a regular user can follow step by step.

Your goal is not to recommend a "single best model." Instead, tell the user:

- Which steps need careful planning
- Which steps can be handed to a cheap/fast model
- Which steps should use tools, tables, tests, or rules to check
- When to escalate to a stronger model
- When automation must stop and let a human decide

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

## Internal analysis

Analyze the task structure internally, but do not output any jargon.

Internal analysis covers:

- Whether the task is easy to verify
- Whether the task is single-step or multi-step
- Whether the task is ambiguous
- Whether it depends on a lot of context or real-time information
- How costly mistakes are
- How reversible mistakes are
- Which steps can be checked by tools
- Which steps need human judgment

## Output requirements

Output only a concise **AI Work Routing**.

Do not output the internal analysis.
Do not pile up jargon.
Do not use specific model names.
Do not say "best model."
Do not make the user feel this is a technical report.
Each step must tell the user: what to do, what to use, why.

## Output format

# AI Work Routing

## One-line strategy

In one sentence a non-technical reader can follow, summarize how this task should be split across a strong model, a cheap model, tools, and humans.

## Recommended steps

Output 5–7 steps. Each step uses this format:

### 1. [Step name]

**What to do:**
One sentence describing what this stage accomplishes.

**What to use:**
Use natural language to describe which capability. Choose only from:

- A strong model planning carefully
- A cheap/fast model executing
- A long-context model reading large material
- A structured-output model organizing into a table / checklist
- A tool / table / test / rule check
- Human judgment

**Why:**
One sentence on why this allocation makes sense.

## Check points

List 3–5 of the most important check points.
Each must be specific and actionable.
Prefer tools, tables, tests, rules, or calculation over asking another AI to judge by feel.

## When to escalate

List specific escalation conditions.
Do not write vague things like "escalate when things get complex."
Write triggers the user can actually judge.

## When to stop automation

List cases that must be handled by a human.
Pay particular attention to real payments, production environments, legal / visa / medical / financial issues, security, privacy, irreversible actions, and unclear user preferences.

## Final deliverable

State what the final output should be so the user can use it directly.

## Output style

- Like work advice for a smart but non-technical user
- Few abstract nouns
- More action verbs
- Keep each step short
- Do not go beyond what the user needs to complete the task

## Length limit

Unless the task is genuinely complex, keep the total output between 700–1000 characters.
Each step's "Why" should be at most one sentence.
```

---

Want the engineer version (full 9 sections, terminology, Agent Instruction)? → [AI Work Routing Card](routing-card.en.md)

## How it works

Different phases of the same task — planning, execution, verification, repair — need different capabilities. Use strong reasoning where direction is unclear or failure is costly. Use cheaper execution where the plan is explicit and mistakes are reversible. Prefer deterministic checks over LLM judgment wherever possible. Escalate when failures repeat, not before.

→ [Routing principles](principles/routing-principles.en.md)

## More examples

- [7-day Japan trip on a budget](examples/japan-trip-7days.en.md)
- [Fitness and diet plan for fat loss](examples/fitness-diet-cut.en.md)
- [Three-month Chinese learning plan (zero to speaking)](examples/chinese-learning-3months.en.md)
- [Industry analysis report: stablecoin on Ethereum](examples/industry-report-stablecoin-eth.en.md)

Each example shows three LLM outputs side by side, collapsed by default.
