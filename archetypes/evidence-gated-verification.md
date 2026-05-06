# Evidence-Gated Verification

**Task type**: Verify that a built artifact matches its specification using captured evidence — not self-report.

The core failure this archetype prevents: agents and developers claiming "zero issues found" or "production ready" based on inspection without proof. First implementations always have issues. Evidence-gated verification defaults to skepticism.

---

## Inputs

- The built artifact (UI, API response, file output, CLI output)
- The original specification (quoted text, not paraphrase)
- An evidence capture method (screenshot tool, test runner output, diff, log)

## Deliverables

A comparison report structured as:

```
Spec says: "[exact quote]"
Evidence shows: [what was actually captured]
Result: PASS / FAIL / PARTIAL
```

For each spec requirement, one evidence entry. No evidence = no claim.

## Verifier

The report is valid when:
- Every claim has a corresponding artifact (screenshot path, test output, log line)
- Spec requirements are quoted, not paraphrased
- Issues are listed with priority (blocking / suggestion / minor)
- Rating is honest: Basic / Good / Excellent — no A+ on first pass

## When to escalate

- Evidence capture fails (Playwright can't reach the app, test runner crashes)
- Spec is ambiguous — two valid readings exist
- "Zero issues found" on a first implementation — look harder before accepting
- Perfect scores (A+, 98/100) on first attempt — these are red flags, not results

## When to stop automation

- Cannot capture evidence programmatically (no screenshot tool, no test runner)
- Spec requirements involve subjective judgment (aesthetic quality, tone, "feels right")
- Artifact requires human interaction to evaluate (accessibility, real-world usability)

## Routing

| Phase | Use |
|---|---|
| Evidence capture | Tool (Playwright, test runner, diff) |
| Comparison | Structured-output model reading spec + evidence |
| Issue prioritization | Strong model if tradeoffs are non-obvious |
| Final approval | Human if issues are blocking or spec is disputed |

---

*Extracted from: Evidence Collector / Reality Checker agent patterns.*
