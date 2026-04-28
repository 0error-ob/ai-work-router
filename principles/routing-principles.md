# Routing Principles

## 1. Route workflows, not prompts

A prompt may contain several kinds of work.

Planning, search, execution, verification, repair, and final packaging may require different model classes or tools.

## 2. Spend strong reasoning where direction matters

Use stronger reasoning when:

- requirements are ambiguous
- task horizon is long
- oracle is weak
- failure cost is high
- context is large
- planning errors are expensive
- the task requires judgment about what should be done

## 3. Use cheaper execution when the work is bounded

Cheaper execution is safer when:

- the plan is explicit
- edit scope is narrow
- output format is constrained
- deterministic verification exists
- failures are reversible
- retry cost is low

## 4. Prefer deterministic verification

If tests, typechecks, schema validation, exact match, lint, or other deterministic checks exist, use them before LLM judgment.

Do not ask another model to judge something that a deterministic verifier can check.

## 5. Escalate on repeated failure

A cheap model may be appropriate for first-pass execution or bounded repair.

Escalate when:

- failures repeat
- root cause is unclear
- scope expands
- output becomes unverifiable
- confidence drops
- failure cost increases

## 6. Do not route from prompt alone when evidence is missing

Some tasks cannot be routed safely from the prompt alone.

Examples:

- model migration decisions
- high-risk production changes
- weak-oracle strategic decisions
- security-sensitive work
- tasks with hidden context

Ask for the missing evidence instead.

## 7. Model names are implementation details

This repo recommends routing policies, not fixed model names.

Model performance, price, and availability change.

Use model classes:

- strong reasoning
- cheap-fast
- coding-capable
- long-context
- structured-output-stable
- multimodal
- deterministic tool
- human review
