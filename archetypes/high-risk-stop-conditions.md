# High-Risk Stop Conditions

**Task type**: Not an archetype for a specific workflow — a set of stop conditions to inject into any routing decision when the task involves regulated domains, irreversible actions, or weak verification.

The core failure this archetype prevents: automation continuing past the point where a human must decide. Most routing cards tell you when to escalate. This card tells you when to stop entirely — regardless of how well the automation is performing.

---

## Universal stop triggers

Stop automation and require human judgment when any of the following are true:

**Irreversibility**
- Action cannot be rolled back (sent email, posted transaction, deleted record, deployed to production)
- Partial cleanup after abort would leave system in inconsistent state

**Weak oracle**
- No deterministic way to verify the output is correct
- Verification requires human judgment ("does this look right?")
- Success criteria are contested or undefined

**High failure cost**
- A wrong output causes financial loss, legal liability, or patient harm
- Recovery from a mistake requires significant human effort or external intervention
- Mistake affects third parties (customers, partners, regulators) not just internal systems

**Regulatory domains**
- Healthcare data (HIPAA) — any automated decision touching patient records requires audit trail and human review path
- Financial transactions above defined thresholds — dual approval required
- Legal documents — no automated generation without human review before signing
- Privacy-regulated data (GDPR, CCPA) — data deletion, export, and processing require compliance review

**Identity and access**
- Granting or revoking permissions in production systems
- Credential creation or rotation affecting live services
- Any action taken "as" another user or service account

**Vendor / contract actions**
- Signing contracts or accepting terms of service
- Committing to spend above approved budget
- Initiating vendor relationships or trials with payment attached

---

## Domain-specific additions

### Compliance / audit context
Stop when:
- A control gap is identified and no compensating control exists
- Evidence of control failure is found — do not attempt automated remediation, escalate
- Audit scope is unclear — do not proceed until scope is defined and approved

### Automation governance context
Stop when:
- Verdict is DEFER or REJECT — do not implement, document the decision
- No owner has been identified for the automation
- Production change requires bypassing a review step (never acceptable)

### Tool selection context
Stop when:
- All candidates fail minimum security requirements — do not choose "least bad" under deadline pressure
- Vendor lock-in terms are unfavorable — do not sign before legal review

---

## Routing when a stop condition is hit

1. Stop the automation
2. Document: what was stopped, why, what state the system is in
3. Notify the responsible human with enough context to make the decision
4. Do not retry automatically — wait for explicit human instruction to resume

---

*Extracted from: Compliance Auditor, Automation Governance Architect, and high-risk domain agent patterns.*
