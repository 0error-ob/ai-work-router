# AI Work Routing Card

Use this template to turn a prompt, task, or work request into a workflow routing policy.

The goal is not to choose one "best model." The goal is to decide where different levels of intelligence, cost, and verification should be used across the workflow.

## 1. Task

Describe the work request in one or two sentences.

## 2. Surface task type

Choose one or more:

- Answer
- Rewrite
- Extract
- Classify
- Generate
- Reason
- Code
- Agentic
- Research
- Data analysis
- Other

## 3. Task-structure profile

### Oracle strength

How will success be checked?

- Strong: tests, schema validation, exact answer, deterministic checker
- Medium: rubric, review, partial validation
- Weak: subjective judgment, open-ended quality, implicit user satisfaction
- None: exploration, brainstorming, unclear target

### Horizon

How many steps are required?

- Single-step
- Short multi-step
- Long-horizon
- Open-ended

### Ambiguity load

How much interpretation is required?

- Low: explicit instruction
- Medium: some judgment required
- High: goal is vague or underspecified

### Context dependency

How much external or local context is required?

- Low: prompt is self-contained
- Medium: needs attached text, files, repo, or references
- High: requires large codebase, long documents, external tools, or historical context

### Output constraint

What form must the output take?

- Freeform text
- Structured JSON/YAML/table
- Executable code
- Patch/diff
- Shell commands
- Decision recommendation
- Public-facing writing

### Failure cost

What happens if the answer is wrong?

- Low: draft, brainstorm, private use
- Medium: internal work product, reviewable output
- High: production code, customer-facing material, financial/legal/security risk

### Reversibility

Can mistakes be rolled back easily?

- Easy
- Moderate
- Hard
- Unknown

## 4. Workflow decomposition

Can the task be decomposed?

- Yes
- No
- Partially
- Unknown

If yes, fill in the phases below.

### Intake / problem understanding

What has to be understood before work begins?

### Planning

Does this require a plan? If yes, what kind?

### Search / context gathering

What information must be found before execution?

### Execution / editing / coding

What concrete work must be done?

### Verification

How should the result be checked?

### Repair / debugging

What should happen if verification fails?

### Final packaging

What final summary, PR note, report, or handoff is needed?

## 5. Recommended routing policy

### Plan

What model class or mode should be used for planning?

Examples:

- strong reasoning model
- regular model
- no separate planning needed
- human planning required

### Execute

What model class or mode should be used for execution?

Examples:

- cheaper coding-capable model
- structured-output-stable model
- long-context model
- deterministic tool
- human execution

### Verify

What verifier should be used?

Prefer deterministic verification when available.

Examples:

- tests
- typecheck
- lint
- schema validation
- exact match
- human review
- stronger model as judge
- not verifiable

### Repair

What should happen after a failed verification?

Examples:

- retry once with same model
- allow two cheap repair attempts
- escalate to stronger reasoning model
- stop and ask human
- roll back

### Finalize

What model class or method should produce the final summary or handoff?

## 6. Escalation triggers

List concrete conditions that require stronger reasoning, human review, or stopping.

Examples:

- tests fail twice
- root cause is unclear
- edit scope expands
- oracle is weak
- task becomes high-risk
- required context is missing
- model starts inventing facts
- output cannot be verified

## 7. Do-not-automate conditions

List cases where automation should not proceed without human input.

Examples:

- ambiguous business decision
- irreversible production action
- missing requirements
- weak oracle + high failure cost
- security-sensitive change
- legal/financial/medical risk
- private data uncertainty

## 8. Rationale

Explain why this routing policy is appropriate.

Focus on task structure, not model brand.
