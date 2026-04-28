# Example: Batch JSON Extraction

## 1. Task

Extract structured fields from 200 customer support messages and output valid JSON.

## 2. Surface task type

- Extract
- Classify
- Structured output

## 3. Task-structure profile

### Oracle strength

Medium to strong.

JSON schema validation can check format. Human sampling may be needed to check semantic accuracy.

### Horizon

Single-step or short multi-step.

### Ambiguity load

Low to medium.

The task is bounded, but some messages may be ambiguous.

### Context dependency

Low.

Each message is mostly self-contained.

### Output constraint

Structured JSON.

### Failure cost

Low to medium.

Individual mistakes are reviewable, but aggregate errors may affect downstream workflow.

### Reversibility

Easy.

Invalid outputs can be retried or corrected.

## 4. Workflow decomposition

### Intake / problem understanding

Define labels and schema.

### Planning

Lightweight planning only. Strong reasoning is usually unnecessary unless the schema is ambiguous.

### Search / context gathering

No external search required.

### Execution / editing / coding

Use a cheap-fast model or structured-output-stable model.

### Verification

Use schema validation.

Sample-check semantic accuracy.

### Repair / debugging

Retry invalid JSON or low-confidence cases.

Escalate ambiguous categories to human review.

### Final packaging

Return valid JSON plus a short summary of error rate and ambiguous cases.

## 5. Recommended routing policy

### Plan

Regular model or human-defined schema.

### Execute

Cheap-fast model or structured-output-stable model.

### Verify

Schema validation first.

Human sample review for semantic quality.

### Repair

Retry invalid JSON.

Escalate ambiguous examples only.

### Finalize

Cheaper model can summarize batch quality.

## 6. Escalation triggers

- Invalid JSON after retry
- Ambiguous category definitions
- High disagreement in sample review
- Output affects high-stakes decision
- Schema changes during the task

## 7. Do-not-automate conditions

- Labels are undefined
- Data contains sensitive private information without safeguards
- Errors would trigger irreversible customer action
- No review process exists for ambiguous cases

## 8. Rationale

This task is a good candidate for cheap execution because it is bounded, high-volume, and partially verifiable. Strong reasoning should be reserved for schema design or ambiguous edge cases, not every extraction.
