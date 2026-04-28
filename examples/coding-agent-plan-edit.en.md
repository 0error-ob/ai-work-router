# Coding Agent Plan/Edit

**Task:** Fix a bug in an existing codebase. Bug report is clear. Repository has tests.

**Task type:** Code, Agentic

## Task-structure profile

| Dimension | Value |
|---|---|
| Oracle strength | Strong — tests, typecheck, lint |
| Horizon | Short multi-step |
| Ambiguity load | Medium — root cause may need investigation |
| Context dependency | Medium-high — needs repo access |
| Output | Patch/diff + PR summary |
| Failure cost | Medium |
| Reversibility | Moderate |

## Routing policy

| Phase | Policy |
|---|---|
| Plan | Strong reasoning if root cause is unclear; lightweight if bug is localized |
| Execute | Cheaper coding-capable model |
| Verify | Tests, typecheck, lint |
| Repair | 1–2 cheap retries; escalate if tests fail twice or scope expands |
| Package | Cheaper model for PR summary |

## Escalation triggers

- Tests fail twice
- Failure points to unrelated subsystem
- More files involved than expected
- Agent proposes broad refactor
- Root cause remains unclear

## Do-not-automate

- Security-sensitive code path
- No tests and high production risk
- Ambiguous requirements
- Change requires product judgment
