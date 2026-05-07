# Failure-Class Routing

**Task type**: Decide what to do after an agent, model, or workflow fails by classifying the failure before retrying.

The core failure this archetype prevents: treating every failure as "use a stronger model" or "try again." Different failure classes need different recovery paths.

---

## Inputs

- The failed run or task attempt
- The expected target state or acceptance condition
- Evidence from the failure: logs, stdout/stderr, traces, tests, screenshots, eval result
- Any known harness or environment constraints

## Deliverables

A failure-routing note:

```text
Failure class: <one or more labels>
Evidence: <log/test/trace snippet>
Likely cause: <why this failed>
Next route: <what to try next>
Do not do: <tempting but wrong retry>
Validation: <how to know the retry worked>
```

## Core Failure Classes

| Failure class | Route | Do not do |
|---|---|---|
| `weak_verifier` | Strengthen verifier against the actual acceptance condition; rerun targeted slice | Do not trust file-exists, process-running, or non-empty-output checks |
| `timeout_budget` | Separate wall-clock, command runtime, model latency, and convergence failure; retry with declared budget change if justified | Do not call timeout a model capability failure without analysis |
| `missing_plan_or_ledger` | Require a brief goal / constraints / verifier / steps ledger before continuing | Do not let the agent keep executing blindly |
| `domain_hard` | Escalate to stronger model, specialist tool, domain playbook, or mark low ROI | Do not spend retries on generic prompt changes |
| `harness_packaging` | Fix build path, executable name, archive layout, environment, or command invocation | Do not edit task logic before the harness is known-good |
| `implementation_mismatch` | Compare expected vs actual behavior; patch the smallest confirmed mismatch | Do not rewrite broad areas without a concrete diff |
| `oracle_or_claim_boundary` | Re-label the run type and evidence surface before reporting | Do not publish as a stronger result than the evidence supports |

## Verifier

The routing note is valid when:

- The failure class is supported by concrete evidence
- The next route changes something relevant to that class
- The validation step is executable or observable
- The public claim boundary is stated if the run will be reported

## When to escalate

- The same failure class repeats after two targeted retries
- The task appears domain-hard rather than scaffold-fixable
- The verifier and official/evaluator result disagree
- The harness conditions differ from the comparison baseline

## When to stop automation

- The next retry would require hidden data, source access, or policy-violating shortcuts
- The failure affects production, money, privacy, safety, or irreversible state
- No reliable verifier can be defined for the next attempt

## Routing

| Phase | Use |
|---|---|
| Evidence collection | Tool logs, traces, tests, screenshots, eval artifacts |
| Failure classification | Structured-output model or rule-based classifier |
| Recovery selection | Router / strong model if tradeoffs are non-obvious |
| Retry execution | Appropriate agent or tool workflow |
| Claim boundary | Eval-claim template before reporting |

---

This archetype is for post-failure routing. It complements pre-task routing cards by deciding what to do after the first attempt produces evidence.
