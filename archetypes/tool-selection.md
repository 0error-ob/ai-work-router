# Tool Selection

**Task type**: Evaluate and recommend a tool or platform using evidence-based scoring, TCO analysis, and vendor risk assessment.

The core failure this archetype prevents: selecting tools based on demos, hype, or familiarity — without testing against real requirements, calculating actual costs, or assessing vendor stability. Poor tool choices waste resources and create migration costs later.

---

## Inputs

- Requirements (functional, integration, security, scale)
- Candidate tools (2–5 options)
- Budget parameters and timeline
- Existing stack constraints (what it must integrate with)

## Deliverables

1. **Scored comparison matrix** — candidates × criteria with weights
2. **3-year TCO breakdown** — licensing + implementation + training + maintenance + migration + support
3. **Vendor risk assessment** — stability, roadmap alignment, exit clause terms
4. **Recommendation** — top-ranked tool with key differentiators and rationale
5. **Pilot plan** — how to validate before full commitment

Evaluation criteria weights (adjust per context):

| Criterion | Default weight |
|---|---|
| Functionality | 25% |
| Usability | 20% |
| Performance | 15% |
| Security | 15% |
| Integration | 10% |
| Support quality | 8% |
| Cost | 7% |

## Verifier

The evaluation is valid when:
- Scores are based on testing with real-world scenarios, not vendor demos
- TCO includes hidden costs (migration, training, change management)
- Vendor claims are validated through independent testing or user references
- A pilot has been defined before full commitment

## When to escalate

- Vendor financial instability identified — requires legal review of contract terms
- Security assessment reveals compliance gaps (SOC 2, HIPAA, etc.)
- Integration testing fails with a critical existing system
- No clear winner — tradeoffs require a business decision, not a technical one

## When to stop automation

- Tool involves handling personal data, financial records, or healthcare information — compliance review required before selection
- Vendor requires data export restrictions or unfavorable lock-in terms — legal review before signing
- All candidates fail minimum security requirements — stop, expand search, do not choose the "least bad" option under pressure

## Routing

| Phase | Use |
|---|---|
| Requirements gathering | Strong model + human stakeholder input |
| Candidate research | Long-context model + web search |
| Scoring matrix | Structured-output model |
| TCO calculation | Tool (spreadsheet/calculator) |
| Security assessment | Specialized model or human security review |
| Final recommendation | Strong model synthesizing all inputs |
| Contract review | Human (legal) |

---

*Extracted from: Tool Evaluator agent patterns.*
