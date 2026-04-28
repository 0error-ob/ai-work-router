# AI Work Routing Card

Route by workflow phase, not by prompt. Fill in each section for your task.

## Task

_One or two sentences._

## Task type

Answer / Rewrite / Extract / Classify / Generate / Reason / Code / Agentic / Research / Data analysis / Other

## Task-structure profile

| Dimension | Value | Notes |
|---|---|---|
| Oracle strength | Strong / Medium / Weak / None | How will success be checked? |
| Horizon | Single-step / Short / Long / Open-ended | |
| Ambiguity load | Low / Medium / High | |
| Context dependency | Low / Medium / High | |
| Output constraint | Freeform / JSON / Code / Patch / Commands / Recommendation / Other | |
| Failure cost | Low / Medium / High | |
| Reversibility | Easy / Moderate / Hard / Unknown | |

## Workflow decomposition

| Phase | Notes |
|---|---|
| Intake | |
| Planning | |
| Search | |
| Execute | |
| Verify | |
| Repair | |
| Package | |

## Routing policy

| Phase | Model class / tool |
|---|---|
| Plan | |
| Execute | |
| Verify | |
| Repair | |
| Finalize | |

_Model classes: strong reasoning · cheaper execution · coding-capable · long-context · structured-output-stable · deterministic verifier · human review_

## Escalation triggers

_Concrete conditions that require stronger reasoning, human review, or stopping._

## Do-not-automate conditions

_Cases where automation must stop and require human input._

## Rationale

_Why this routing policy fits this task structure._
