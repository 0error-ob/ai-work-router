# Automation Governance

**Task type**: Decide whether to approve, pilot, partially automate, defer, or reject an automation request — before any implementation begins.

The core failure this archetype prevents: automating things just because they're technically possible. Low-value or unsafe automations create operational debt, compliance risk, and systems nobody understands when they break.

---

## Inputs

- Automation proposal (what process, what tool, what scope)
- Four mandatory dimensions:
  1. **Time savings per month** — is it recurring and material? does frequency justify overhead?
  2. **Data criticality** — customer, finance, contract, scheduling records involved? impact of wrong/delayed/duplicated data?
  3. **External dependency risk** — how many external APIs? are they stable, documented, observable?
  4. **Scalability (1x to 100x)** — will retries, deduplication, rate limits hold under load?

## Deliverables

Exactly one verdict:

| Verdict | Meaning |
|---|---|
| **APPROVE** | Strong value, controlled risk, maintainable architecture |
| **APPROVE AS PILOT** | Plausible value, limited rollout required first |
| **PARTIAL AUTOMATION ONLY** | Automate safe segments, keep human checkpoints |
| **DEFER** | Process not mature, value unclear, or dependencies unstable |
| **REJECT** | Weak economics or unacceptable operational/compliance risk |

Every verdict must include:
- Fallback path (what happens when the automation fails)
- Ownership (who is responsible for this automation)
- For APPROVE: reliability baseline requirements (see below)

## Reliability baseline (required for APPROVE)

Every approved automation must have:
- Explicit error branches
- Idempotency or duplicate protection where relevant
- Safe retries with stop conditions (not infinite retry loops)
- Timeout handling
- Alerting behavior
- Manual fallback path

Logging minimum: workflow name + version, execution timestamp, source system, affected entity ID, success/failure state, error class.

## Verifier

Before production:
- Happy path test passed
- Error branch test passed
- Documentation exists

"Done" status requires documentation AND test evidence. Not one or the other.

## When to escalate

- Direct live changes to critical production flows — require explicit approval, not assumption
- External dependency is undocumented or has no SLA
- Data criticality is high and recovery from wrong/duplicated data is expensive or impossible

## When to stop automation

- Verdict is REJECT or DEFER — stop, do not implement, document why
- Automation involves payments, legal records, or healthcare data without explicit compliance review
- "Clever and fragile" beats "simple and robust" in the proposed design — reject and redesign
- No owner identified — automation with no owner will not be maintained

## Routing

| Phase | Use |
|---|---|
| Dimension assessment | Strong model |
| Verdict decision | Strong model + human review if data criticality is high |
| Reliability baseline design | Coding-capable model |
| Test evidence | Tool (automated test runner) |
| Production approval | Human sign-off required |

---

*Extracted from: Automation Governance Architect agent patterns.*
