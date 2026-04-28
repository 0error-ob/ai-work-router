# Example: Coding Agent Plan/Edit Workflow

## 1. Task

Modify a small part of an existing codebase according to a clear bug report. The repository has tests.

## 2. Surface task type

- Code
- Agentic

## 3. Task-structure profile

### Oracle strength

Strong.

The result can be checked with tests, typecheck, and lint.

### Horizon

Short multi-step.

The workflow requires understanding the bug, locating relevant files, editing code, running tests, and repairing failures.

### Ambiguity load

Medium.

The bug report is clear, but root cause may require investigation.

### Context dependency

Medium to high.

The agent needs access to the repository and related files.

### Output constraint

Patch/diff and possibly a short PR summary.

### Failure cost

Medium.

The change is reviewable and tests exist, but incorrect edits could break behavior.

### Reversibility

Moderate.

Changes can be reverted, but debugging time may grow if edits spread.

## 4. Workflow decomposition

### Intake / problem understanding

Read the bug report and identify expected behavior.

### Planning

Use a strong reasoning model if the root cause is unclear or multiple files may be involved.

### Search / context gathering

Use tool-assisted search to locate relevant files, tests, and references.

### Execution / editing / coding

Use a cheaper coding-capable model once the plan and edit scope are clear.

### Verification

Run tests, typecheck, and lint.

### Repair / debugging

Allow one or two repair attempts with the same execution model if failures are local and understandable.

Escalate if failures repeat or the root cause becomes unclear.

### Final packaging

Use a cheaper model to summarize the change after verification passes.

## 5. Recommended routing policy

### Plan

Strong reasoning model when the cause is unclear.

If the bug is already localized, planning can be lightweight.

### Execute

Cheaper coding-capable model for bounded edits.

### Verify

Deterministic tools:

- tests
- typecheck
- lint

### Repair

One or two cheap repair attempts.

Escalate to stronger reasoning if tests fail twice, root cause is unclear, or edit scope expands.

### Finalize

Cheaper model for PR summary.

## 6. Escalation triggers

- Tests fail twice
- Failure message points to unrelated subsystem
- More files become involved than expected
- Agent proposes broad refactor
- No deterministic test covers the changed behavior
- Root cause remains unclear

## 7. Do-not-automate conditions

- Security-sensitive code path
- No tests and high production risk
- Requirements are ambiguous
- Change requires product judgment
- Patch touches critical infra without review

## 8. Rationale

This workflow can save cost by separating planning from bounded execution.

Strong reasoning is valuable when deciding where and how to change the code. Once the plan is clear and tests exist, cheaper execution is safer. Deterministic verification should be the main judge.
