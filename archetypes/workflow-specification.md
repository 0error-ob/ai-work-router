# Workflow Specification

**Task type**: Map all paths through a system before any implementation begins — happy paths, failure modes, recovery actions, timeouts, and handoff contracts.

The core failure this archetype prevents: systems that break at step 7 of 12 because no one asked "what happens if step 4 takes longer than expected?" Undocumented implicit workflows cause bugs, data loss, and security failures. Mapping replaces prose with a tree that agents can implement against and QA can test against.

---

## Inputs

- Product intent (what the system is supposed to do)
- System context (existing services, APIs, external dependencies)
- Known constraints (SLAs, data types, user roles)

## Deliverables

A complete workflow tree. For each workflow:

```
Workflow: [name]
Trigger: [what starts it]
Happy path: [step 1 → 2 → ... → terminal state]
Branch conditions: [at each decision node: condition → path]
Failure modes: [what can go wrong at each step]
Recovery actions: [what happens when failure occurs]
Timeout handling: [what happens if step N takes too long]
Partial cleanup: [what state needs to be rolled back if aborted mid-flow]
Handoff contract: [what the next system/human receives, in what format, under what guarantees]
Observable states: [what external observers can see at each point]
```

Nothing built until all paths documented.

## Verifier

The spec is complete when:
- QA can write test cases against it without asking clarifying questions
- Every decision node has explicit branch conditions (no "otherwise" left implicit)
- Every failure mode has a named recovery action (not just "handle errors")
- Every handoff defines the contract: format, guarantees, failure behavior
- Timeout and partial cleanup paths exist for every multi-step flow

## When to escalate

- A workflow is discovered mid-spec that nobody mentioned (implicit workflows are the most dangerous)
- A decision node's conditions are business logic that hasn't been decided yet
- External API behavior is undocumented or unreliable
- "What happens if step 4 takes longer than expected?" has no answer

## When to stop automation

- Business rules at a branch are contested or undecided — stop, get the decision, then resume
- The workflow involves irreversible external actions (payments, emails sent, legal records) — require explicit human sign-off on the spec before implementation begins
- Handoff contract depends on a system whose behavior is unknown

## Routing

| Phase | Use |
|---|---|
| Initial workflow discovery | Strong model (ambiguity is high, missing paths are expensive) |
| Branch condition enumeration | Strong model + human review for business logic |
| Failure mode / recovery mapping | Strong model |
| Spec documentation | Structured-output model |
| Spec review | Human (QA or system owner) before implementation begins |

---

*Extracted from: Workflow Architect agent patterns.*
