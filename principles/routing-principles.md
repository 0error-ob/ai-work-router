# Routing Principles

## Route workflows, not prompts

Planning, search, execution, verification, repair, and packaging may each require different model classes or tools.

## Spend strong reasoning where direction matters

- requirements are ambiguous
- task horizon is long
- oracle is weak
- failure cost is high
- planning errors are expensive

## Use cheaper execution when work is bounded

- plan is explicit
- edit scope is narrow
- deterministic verification exists
- failures are reversible

## Prefer deterministic verification

Use tests, typecheck, schema validation, lint, or exact match before LLM judgment.

## Escalate on repeated failure

- failures repeat
- root cause is unclear
- scope expands
- failure cost increases

## Do not route from prompt alone when evidence is missing

Model migration, high-risk production changes, security-sensitive work, tasks with hidden context — ask for missing evidence instead.

## Model names are implementation details

Use model classes: strong reasoning · cheap-fast · coding-capable · long-context · structured-output-stable · deterministic tool · human review
