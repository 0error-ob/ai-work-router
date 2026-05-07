# Knowledge-Routed Scaffold

**Task type**: Assemble a small, task-specific workflow from a larger library of lessons, playbooks, and failure patterns.

The core failure this archetype prevents: loading every past lesson into every task until the scaffold becomes too large, stale, and internally contradictory.

---

## Inputs

- Task description
- Task profile: domain, tools, evidence surface, input/output surface, verification surface
- Available lesson library or playbook set
- Known budget and risk constraints
- Any prior run evidence or failure classes

## Deliverables

A scaffold pack:

```text
Task profile: <short structured profile>
Selected lessons: <5-9 lessons, each with reason>
Excluded lessons: <important non-applicable lessons>
Verifier shape: <how success will be checked>
Escalation triggers: <when to use stronger model/tools/human>
Stop conditions: <when automation should pause>
Trace artifacts: <what must be recorded>
```

## Routing Principle

Do not treat experience as a single prompt.

Use this flow:

```text
task profile
-> match relevant lessons
-> assemble small scaffold pack
-> run
-> classify failures
-> update lessons
```

The lesson library can grow large. The active scaffold should stay small.

## Lesson Selection

| Lesson scope | Include when | Exclude when |
|---|---|---|
| Universal evidence discipline | Almost always | Only for tiny one-shot tasks where trace is unnecessary |
| Task-family lesson | The task family matches | The task merely shares surface vocabulary |
| Language/runtime lesson | The runtime behavior is present | The language or runtime differs |
| Domain lesson | The domain object is central to the task | It is only an analogy |
| Benchmark/harness lesson | The same harness or evidence surface is in use | Public claim would become misleading |

## Verifier

The scaffold pack is valid when:

- selected lessons each name why they apply;
- excluded lessons name why they do not apply;
- the verifier checks the actual acceptance condition;
- the trace artifacts are enough to reconstruct the run;
- the claim boundary is explicit if the result will be reported.

## When to escalate

- More than 9 lessons appear necessary and cannot be split by phase
- Two selected lessons give conflicting advice
- The evidence surface changes mid-run
- The verifier cannot be made task-specific
- A repeated failure class persists after two targeted retries

## When to stop automation

- The only next step requires hidden data, privileged artifacts, or disallowed source access
- The scaffold cannot define a reliable verifier
- The task enters a regulated, irreversible, privacy-sensitive, financial, legal, medical, or production-risk domain

## Relation To Other Archetypes

- Use **Failure-Class Routing** after a failed run.
- Use **Evidence-Gated Verification** when the main risk is proof quality.
- Use **High-Risk Stop Conditions** as a cross-cutting guardrail.

This archetype is not a benchmark-specific trick. It is a way to keep learned workflow knowledge useful without turning the prompt into an unfiltered memory dump.
