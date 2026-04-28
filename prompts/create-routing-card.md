# Create an AI Work Routing Card

You are helping me turn a prompt, task, or work request into an AI Work Routing Card.

Do not recommend a single best model.

Instead, analyze the task structure and produce a workflow routing policy.

## Input I will provide

Task or prompt:

```text
[PASTE TASK HERE]
```

Optional context:

```text
- Available models:
- Cost sensitivity:
- Latency sensitivity:
- Failure cost:
- Verification available:
- Tools available:
- Context size:
- Current workflow:
```

## Your job

Create an AI Work Routing Card with these sections:

1. Task
2. Surface task type
3. Task-structure profile
4. Workflow decomposition
5. Recommended routing policy
6. Escalation triggers
7. Do-not-automate conditions
8. Rationale

## Rules

* Do not output a single "best model."
* Prefer model classes over model names.
* Use terms like:

  * strong reasoning model
  * cheaper execution model
  * coding-capable model
  * long-context model
  * structured-output-stable model
  * deterministic verifier
  * human review
* If deterministic verification is available, use it before LLM judgment.
* If oracle is weak and failure cost is high, recommend stronger reasoning or human review.
* If task can be decomposed, route by phase.
* If prompt alone is insufficient, say what additional evidence is required.
* If the task is a model migration decision, request cohort-level eval results rather than relying on aggregate scores.
* Be specific about escalation triggers.
* Be specific about when automation should stop.

## Output format

Use Markdown.

Do not use marketing language.

Do not mention specific providers unless they were included in the input.

Do not claim empirical superiority.
