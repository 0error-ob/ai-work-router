# Batch JSON Extraction

**Task:** Extract structured fields from 200 customer support messages. Output valid JSON.

**Task type:** Extract, Classify, Structured output

## Task-structure profile

| Dimension | Value |
|---|---|
| Oracle strength | Medium-strong — schema validation + human sample |
| Horizon | Single-step |
| Ambiguity load | Low-medium — some messages may be ambiguous |
| Context dependency | Low — self-contained messages |
| Output | Structured JSON |
| Failure cost | Low-medium |
| Reversibility | Easy |

## Routing policy

| Phase | Policy |
|---|---|
| Plan | Regular model or human-defined schema |
| Execute | Cheap-fast or structured-output-stable model |
| Verify | Schema validation first; human sample for semantic quality |
| Repair | Retry invalid JSON; escalate ambiguous cases only |
| Package | Cheaper model — error rate summary + ambiguous case list |

## Escalation triggers

- Invalid JSON after retry
- Ambiguous category definitions
- High disagreement in sample review
- Schema changes during the task

## Do-not-automate

- Labels undefined
- Sensitive data without safeguards
- Errors trigger irreversible customer action
- No review process for ambiguous cases
