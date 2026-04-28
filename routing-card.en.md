Analyze an AI work task and produce an executable workflow routing strategy.

Your goal is not to recommend a "single best model." Instead, determine:

- Which phases warrant strong reasoning
- Which phases can use cheaper execution
- Which phases should prioritize deterministic verifiers
- When to escalate, stop, or require human review
- Whether this task is suitable for automation

## Task

[Paste task description here]

## Optional context

- Cost sensitivity:
- Failure cost:
- Verification available:
- Tools available:
- Context size:
- Involves code / files / external pages / data:
- Current workflow or known pain points:

## Output requirements

Produce output following the 9-section structure below.

---

# AI Work Routing Card

## 1. Task

Restate the task in 1–2 sentences.
Do not expand or add goals the user did not provide.

## 2. Task type

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
- Decision
- Other

## 3. Task-structure profile

Assess each dimension with one sentence of reasoning:

- Oracle strength: Strong / Medium / Weak / None
- Horizon: Single-step / Short multi-step / Long-horizon / Open-ended
- Ambiguity load: Low / Medium / High
- Context dependency: Low / Medium / High
- Output constraint: Freeform / Structured output / Executable code / Patch / Decision recommendation / Public-facing text
- Failure cost: Low / Medium / High
- Reversibility: Easy / Moderate / Hard / Unknown
- Cost sensitivity: Low / Medium / High

## 4. Workflow decomposition

Decompose the task by phase.
If a phase is not needed, write "Not needed" and explain why.

### Intake / Understanding the task
- Goal:
- Recommended routing:
- Reasoning:

### Plan / Planning
- Goal:
- Recommended routing:
- Reasoning level:
- Reasoning:

### Search / Context gathering
- Goal:
- Recommended routing:
- Reasoning:

### Execute / Execution
- Goal:
- Recommended routing:
- Reasoning level:
- Reasoning:

### Verify / Verification
- Goal:
- Preferred verification method:
- Prioritize deterministic verifier:
- Reasoning:

### Repair / Fixing
- Trigger condition:
- Recommended routing:
- Escalation condition:

### Package / Delivery
- Output form:
- Recommended routing:
- Reasoning:

## 5. Routing policy by phase

Output as a table:

| Phase | Recommended model / tool class | Reasoning level | Specific action | Why |
|---|---|---|---|---|

Choose only from these model classes — do not use specific model names:

- Strong reasoning
- Cheaper execution
- Coding-capable model
- Long-context model
- Structured-output-stable model
- Deterministic verifier
- Human review

Notes:

- When a deterministic verifier is available, do not default to LLM judgment.
- When a task can be split into plan / execute / verify, do not hand the whole task to one model.
- If the prompt alone is insufficient for routing, say explicitly what information is missing.

## 6. Escalation triggers

List concrete, actionable escalation conditions.

Examples:

- Tests fail twice in a row
- Root cause is unclear
- Edit scope expands
- Oracle weakens
- Task shifts from low-risk to high-risk
- Required context is missing
- Output cannot be verified
- Model starts fabricating facts

Do not write vague conditions like "escalate when things get complex."

## 7. Stop / do-not-automate conditions

List when automation must stop and require human input.

Pay particular attention to:

- Weak oracle + high failure cost
- Irreversible actions
- Security / legal / financial / medical risk
- Requirements are unclear
- Critical context is missing
- No verification method exists
- Execution affects real users or production environment

## 8. Agent Instruction

Produce a short instruction block that can be copied directly to a coding agent or AI agent.

Requirements:

- No more than 10 lines
- Use imperative language
- Define clear boundaries for plan / execute / verify / repair
- State explicitly when to escalate or stop
- Do not use specific model names

## 9. Rationale

Explain the core logic of this routing strategy in 3–5 sentences.

Focus on:

- Why strong reasoning should be spent on these phases
- Why cheaper execution is safe for certain phases
- How verification reduces risk
- When automation should not continue
