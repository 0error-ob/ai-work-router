# Model Migration Decision

**Task:** Decide whether to migrate a coding-agent workflow to a cheaper model.

**Task type:** Reason, Migration decision

## Task-structure profile

| Dimension | Value |
|---|---|
| Oracle strength | Weak without cohort-level eval data |
| Horizon | Long-horizon — affects many future tasks |
| Ambiguity load | High — "better" has many dimensions |
| Context dependency | High — needs eval results, cohorts, cost data, rollback plan |
| Output | Decision recommendation + rollout policy |
| Failure cost | High |
| Reversibility | Moderate — requires prepared fallback |

## Routing policy

| Phase | Policy |
|---|---|
| Plan | Strong reasoning or human-led |
| Execute | Route migration-safe cohorts first; do not switch full workflow |
| Verify | Cohort-level success, failure breakdown, cost per accepted result |
| Repair | Keep fallback to current model; escalate when weak-oracle tasks fail |
| Package | Staged migration recommendation with rollback conditions |

## Escalation triggers

- Candidate regresses on weak-oracle cohorts
- Debugging loops increase
- Cost per accepted result rises despite lower token price
- Long-context tasks degrade
- Rollback path is unclear

## Do-not-automate

- Only aggregate score available
- No failure breakdown
- No rollback plan
- Task cohorts not separated
