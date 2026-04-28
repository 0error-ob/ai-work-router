# AI Work Router

A lightweight framework for turning prompts and work requests into workflow routing policies.

Most routing asks: which model should handle this prompt?

AI Work Router asks: where is intelligence actually needed in this workflow?

## What this is

A template and prompt system for producing AI Work Routing Cards.

It helps you decide:

- where to use strong reasoning
- where cheaper execution is safe
- what verifier should be used
- when to escalate
- when not to automate

## What this is not

- not a model recommender
- not a benchmark
- not a leaderboard
- not a provider router
- not a cost optimizer
- not a claim that any specific model is best

## One-minute example

Task:

> Modify a small function according to an explicit plan and run tests.

Routing policy:

- Plan: already provided, no strong planning needed
- Execute: cheaper coding-capable model is acceptable
- Verify: run tests / typecheck
- Repair: allow one cheap repair attempt
- Escalate: use stronger reasoning if tests fail twice or root cause is unclear

## Core idea

Do not route the whole prompt as one unit.

Route the workflow by phase:

1. Intake
2. Planning
3. Search / context gathering
4. Execution / editing / coding
5. Verification
6. Repair / debugging
7. Final packaging

## Use cases

Use this repo when you need to:

- decide which parts of a coding task need a stronger model
- reduce token cost without blindly downgrading the whole workflow
- create a routing policy for an agent workflow
- decide whether a task is safe to automate
- separate planning, execution, verification, and repair
- write a model migration recommendation by workflow phase

## Start here

- Template: `templates/ai-work-routing-card.md`
- Prompt: `prompts/create-routing-card.md`
- Examples: `examples/`

## Roadmap

v0 is Markdown-only.

Future versions may explore:

- interactive card generation
- local CLI
- BYOK app
- feedback-based routing logs

Only add these after real external usage signals.
