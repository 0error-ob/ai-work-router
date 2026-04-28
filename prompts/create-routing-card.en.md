# Create an AI Work Routing Card

Analyze the task structure and produce a workflow routing policy. Do not recommend a single best model.

## Task

```text
[PASTE TASK HERE]
```

## Optional context

```text
- Cost sensitivity:
- Failure cost:
- Verification available:
- Tools available:
- Context size:
```

## Output

Produce a completed AI Work Routing Card:

1. Task
2. Task type
3. Task-structure profile (oracle strength, horizon, ambiguity, context dependency, output constraint, failure cost, reversibility)
4. Workflow decomposition (intake → plan → search → execute → verify → repair → package)
5. Routing policy by phase
6. Escalation triggers
7. Do-not-automate conditions
8. Rationale

Use model classes, not model names: strong reasoning · cheaper execution · coding-capable · long-context · structured-output-stable · deterministic verifier · human review.

Prefer deterministic verification over LLM judgment. If evidence is insufficient, say what's missing. Be specific about escalation triggers and stop conditions.
