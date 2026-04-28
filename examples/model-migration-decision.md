# Example: Model Migration Decision

## 1. Task

Decide whether to migrate a coding-agent workflow from a current expensive model to a cheaper candidate model.

## 2. Surface task type

- Reason
- Code
- Model comparison
- Migration decision

## 3. Task-structure profile

### Oracle strength

Weak unless cohort-level eval data is available.

Aggregate success rate alone is not enough.

### Horizon

Long-horizon.

Migration affects many future tasks and workflows.

### Ambiguity load

High.

"Better" may mean cost, latency, success rate, failure rate, repairability, or user trust.

### Context dependency

High.

Requires eval results, task cohorts, cost data, failure examples, and rollback plan.

### Output constraint

Decision recommendation and rollout policy.

### Failure cost

High.

A bad migration can reduce output quality, increase debugging time, or harm production workflows.

### Reversibility

Moderate.

Migration can be rolled back, but only if routing, logging, and fallback are prepared.

## 4. Workflow decomposition

### Intake / problem understanding

Clarify why migration is being considered:

- cost reduction
- latency
- availability
- quality
- provider risk
- workflow fit

### Planning

Use a strong reasoning model or human review.

Migration should not be decided from a prompt alone.

### Search / context gathering

Collect cohort-level evals:

- test-backed bug fixes
- weak-oracle planning tasks
- long-context repo navigation
- structured edits
- repair loops
- cost per successful task

### Execution / editing / coding

No direct execution until migration-safe cohorts are identified.

### Verification

Use cohort-level success, failure mode breakdown, cost per accepted result, and rollback tests.

### Repair / debugging

If candidate model underperforms in a cohort, keep current model or route only safe sub-cohorts.

### Final packaging

Produce a migration note with staged rollout and rollback conditions.

## 5. Recommended routing policy

### Plan

Strong reasoning or human-led planning.

### Execute

Do not switch the full workflow.

Route only migration-safe cohorts first.

### Verify

Cohort-level evals, not aggregate score.

### Repair

Keep fallback to current model.

Escalate to stronger model when weak-oracle tasks fail or repair loops increase.

### Finalize

Write a staged migration recommendation.

## 6. Escalation triggers

- Candidate model regresses on weak-oracle cohorts
- Debugging loops increase
- Cost per accepted result rises despite lower token price
- Long-context tasks degrade
- Human review burden increases
- Rollback path is unclear

## 7. Do-not-automate conditions

- Only aggregate score is available
- No failure breakdown exists
- No rollback plan exists
- Production risk is high
- Task cohorts are not separated
- Quality cannot be verified

## 8. Rationale

A model migration decision should not be treated as a single prompt-routing problem.

The right unit is the task cohort. A cheaper model may be safe for test-backed bounded edits but unsafe for long-horizon planning or weak-oracle tasks. The routing policy should migrate by cohort, preserve fallback, and define rollback conditions.
