# Codebase Context Reconstruction

**Task type**: Build an accurate mental model of an unfamiliar codebase by reading source code, tracing execution paths, and stating only facts grounded in inspected files.

The core failure this archetype prevents: agents and developers making claims about how a codebase works based on inference, naming conventions, or assumed patterns — without inspecting the actual code. Incorrect mental models cause wrong edits in wrong files, missed entry points, and cascading bugs.

---

## Inputs

- Repository (read-only access)
- Specific question or onboarding goal (optional — defaults to full orientation)

## Deliverables

Three-level explanation, in order:

**Level 1 — One-line summary**
What this codebase is, in one sentence.

**Level 2 — Five-minute explanation**
- Primary tasks the code performs
- Primary inputs (HTTP requests, CLI args, events, files, function calls)
- Primary outputs (responses, DB writes, files, events, rendered UI)
- Key files and their responsibilities
- Main code paths: entry → orchestration → core logic → outputs

**Level 3 — Deep dive**
- Runtime(s) and framework(s) — identified from manifests, not assumed
- Entry points: specific file paths and why they matter
- Top-level directory map: path → purpose
- Key module boundaries: presentation / application / persistence / cross-cutting
- Execution traces: concrete step-by-step path for at least one primary flow
- Files inspected (explicit list) and files not inspected (explicit acknowledgment)

## Verifier

The output is valid when:
- Every claim about behavior references a specific file, function name, or route
- "I inspected X; I did not inspect Y" is stated explicitly
- No inferred intent ("this module probably handles...") — only observed behavior
- A new developer can identify main entry points within 5 minutes of reading the output

## When to escalate

- Answer is partial after one subsystem — acknowledge the limit, don't generalize
- Naming is misleading (a module named "manager" that acts as a service layer) — surface the discrepancy
- Dead code, deprecated abstractions, or migration artifacts are present — flag them explicitly

## When to stop automation

- Never suggest code changes, improvements, or refactors — stop at description
- Never claim full understanding after inspecting one subsystem
- Never infer intent, quality, or future plans from code structure
- If a file was not inspected, do not make claims about it

## Scope boundary

This archetype is **read-only**. Its only output is understanding.

When the task shifts from understanding to modifying — writing a patch, fixing a bug, adding a feature — exit this archetype and switch to a coding or verification workflow. Do not blend the two: context reconstruction that slides into code editing loses the discipline that makes both reliable.

## Routing

| Phase | Use |
|---|---|
| Manifest and entry point inventory | Coding-capable model (read-only) |
| Execution path tracing | Coding-capable model |
| Level 1 + 2 summary | Structured-output model |
| Level 3 deep dive | Long-context model (large repos) |
| Validation | Human developer confirms entry points are correct |

---

*Extracted from: Codebase Onboarding Engineer and LSP Index Engineer agent patterns.*
