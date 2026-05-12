# Schemas

Machine-readable counterpart to the prompt-form [routing-card](../routing-card.md).

The card produces a routing plan for a human to read. The schema captures the same plan in a form an agent system can consume and a harness can validate. Both express the same routing logic; pick the form that matches your downstream consumer.

---

## What's here

- [task-routing.schema.yaml](./task-routing.schema.yaml) — phase-by-phase routing plan with role, output kind, ledger writes, and escalation triggers. Documented human-readable form.
- [task-routing.schema.json](./task-routing.schema.json) — machine-consumable form of the same schema. Kept in sync with the YAML. Agents and harnesses should read this one (no YAML parser needed).

---

## Why both forms

The routing-card is what you write at the start of a project, by hand or with a stronger model, when you need to think clearly about which phases of a task need strong reasoning vs cheap execution vs deterministic verification. Its consumer is a person making a design decision.

The schema is what an agent or harness consumes at runtime, on every task, to know which resource each phase should call and what ledger fields each phase must produce. Its consumer is software.

A team will typically write the card once per task class, then express the result as a schema that gets reused across all tasks in that class.

---

## Phase roles

The schema's `role` enum names the resource class for each phase. It deliberately does not name specific models:

| Role | Meaning |
|------|---------|
| `strong_reasoning` | Phase needs careful reading or planning. |
| `incremental_action` | Phase advances the state with bounded steps. |
| `tool_validation` | Phase relies on a deterministic check, not on model judgment. |
| `gate` | Phase consults explicit conditions to allow or block continuation. |
| `human_review` | Phase requires a person. |
| `cheap_execution` | Phase is repetitive and safe to route to a cheaper resource. |

A scaffold or harness reading this schema maps these roles to whatever model / tool / human-routing it uses internally. The schema does not pin those decisions.

---

## Relationship to other schemas

The `ledger_writes` field in each phase names entries in the [agent-run-ledger schema](https://github.com/0error-ob/eval-claim/blob/main/schemas/agent-run-ledger.schema.json). A scaffold producing a ledger should populate the fields the schema declares for each phase before transitioning.

The two schemas together describe a minimum runtime contract: routing tells the agent *what each phase must do*; ledger captures *what each phase did*. A claim card later cites the ledger; the linter checks alignment.

---

## How to use

A scaffold integration typically:

1. Loads the schema once at task start.
2. Reads the `agent_instruction` field into the agent's prompt.
3. After each phase output, validates that the declared `ledger_writes` fields are present.
4. Triggers the corresponding `escalate_when` action if any condition matches the agent's recent behavior.

A 5-line proof-of-concept integration is sufficient to verify that the schema is being consumed rather than ignored. Anything more elaborate is a design choice, not a requirement of the schema.

---

## Versioning

Schema is at `v0`. Field renames and additions are allowed without notice during v0. A v1 will pin field names.

Role enum values are tracked in this file. Adding a role requires adding it to the table above and to any tooling that consumes the schema.
