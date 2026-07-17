---
name: product-grill-me
description: A grilling session that frames every decision in the product scenario it affects.
disable-model-invocation: true
---

Run a `/grilling` session, working every decision from the product inward.

## Establish the scenario

Before the first question, assemble the product context from the conversation, product docs, the issue or spec, the codebase, and available tools. Ask only for the smallest missing detail needed to name:

- who the user is and what they are trying to accomplish
- where the flow begins and the path they take
- what success and failure look like to them
- which product promise or constraint makes this work matter

## Sort every candidate question

Before asking anything, apply one test: **would anyone outside the codebase notice the difference?** A user, a support ticket, a demo, a bill, an SLA — through latency, cost, reliability, or what appears on screen.

- Someone notices → it is a product decision. Grill it, using the shape below.
- Nobody notices → it is an implementation detail. Investigate or decide it yourself, and log the call in one line for the walkthrough.

Order the product decisions by user stakes: start where the flow's promises are most at risk, not where the system is most interesting.

## Question shape

1. **Scenario** — the user, their goal, and the concrete flow, in plain language.
2. **Problem** — what is broken, risky, slow, confusing, or newly required in that flow.
3. **Options** — each candidate behaviour traced round-trip: from the user's action to the system responsibility, and from the internal mechanism back to the visible outcome. Explain only the mechanism needed to make the behaviour real.
4. **Recommendation** — your pick, with its customer impact and its internal trade-off.
5. **Question** — ask for one decision in ordinary language, defining any unavoidable technical term immediately. Then wait.

Prefer concrete cause and effect over labels. Not "Should orchestration use durable checkpoints?" but: a customer starts a 30-minute run, a worker restarts at step 18, and they expect the same run to continue — saving progress after each step makes that possible. Is preserving the run worth the added storage and recovery complexity?

## Close with a walkthrough

The session is done when every decision is either answered by the user or logged as an implementation call. Close by replaying the flow as it will now behave — the user's journey through the resolved plan — followed by the one-line log of calls you made on your own, so the user can veto any of them.
