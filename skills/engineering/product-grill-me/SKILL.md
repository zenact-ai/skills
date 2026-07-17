---
name: product-grill-me
description: Make technical decisions easier by grounding them in product, implementation, priority, and existing code patterns.
disable-model-invocation: true
---

Run a `/grilling` session centred on one concrete product scenario. Trace how the system implements that scenario end to end, then grill the unresolved technical choices along that path.

Never ask a naked technical question. A decision is only ready to ask once the context that makes it understandable and comparable has been supplied.

Build four kinds of context from the conversation, product docs, issue, spec, codebase, and available tools:

1. **Product context** — Who the user is, what they are trying to accomplish, where the flow begins, what they experience, and what success or failure means to them.
2. **Technical context** — Where this decision sits in the implementation path, what the system does today, which components and data are involved, and which constraints or failure modes shape the choice.
3. **Prioritisation context** — Why this matters now, what outcome has priority, what can be deferred, and whether the current bias is speed, correctness, reliability, latency, cost, security, maintainability, or future flexibility.
4. **Patterns context** — How analogous behaviour is implemented, tested, and operated elsewhere in the codebase; which conventions are deliberate; and whether this decision should follow them or intentionally diverge.

Find this context yourself wherever the environment can answer it. Cite concrete files, modules, tests, or existing flows when explaining a codebase pattern. Distinguish a documented convention from a pattern that merely happens to appear once. If a consequential piece of context is missing, ask only for that missing piece before presenting the decision.

Keep one product scenario fixed as the spine of the session. Once its user, goal, path, success and failure conditions, and relevant product promise are clear, spend most of the session at the technical implementation level. The product scenario anchors the discussion; the other three contexts make each implementation decision easier to evaluate.

Before asking the first decision, build a compact implementation path for the scenario:

1. the user action or external trigger
2. the system entry point that receives it
3. the components, calls, and data transformations that carry it forward
4. the state that is created, changed, or persisted
5. any asynchronous work, waiting, or external dependency
6. failure, retry, duplicate, timeout, and recovery behaviour
7. the result that returns to the product and becomes visible to the user

When a codebase exists, trace the actual code path instead of inventing an idealised architecture. Separate what the code proves, what you infer, and what remains unknown. Find facts yourself; put decisions to the user.

Walk the implementation path in execution order. At each unresolved point, ask one question using this shape:

1. **Product context** — Remind the user, compactly, which customer flow and visible outcome this step serves.
2. **Technical context** — Explain where the implementation is now, what happens internally, and which constraint or gap creates the decision.
3. **Prioritisation context** — State what the choice should optimise for now and which concerns are secondary or deferrable.
4. **Existing pattern** — Show how the codebase handles the closest analogous case and whether following it is appropriate here.
5. **Approaches** — Present the viable choices in concrete cause-and-effect terms.
6. **Recommendation** — Recommend one approach using all four contexts, including the reason to preserve or break from the existing pattern.
7. **Question** — Ask for the single decision that unblocks the next part of the path, then wait.

Keep this frame compact and decision-specific. Context is not ceremonial boilerplate: include the facts that materially change the choice, omit unrelated background, and state explicitly when one of the four contexts is unknown or not material.

Keep drilling into the implementation where the scenario demands it: ownership boundaries, state transitions, storage, synchronous versus asynchronous work, failure recovery, observability, rollout, compatibility, and testing. Do not turn this into a generic architecture review; only pursue a branch when it helps explain or safely deliver the scenario.

Trace each option in both directions: from the user's action to the system responsibility, and from the proposed mechanism back to the visible product outcome. Treat a choice as decision-worthy when it materially affects the product's correctness, reliability, latency, cost, security, delivery priority, consistency, or ability to evolve. Resolve purely local implementation details autonomously.

Prefer concrete cause and effect over labels. Instead of asking, “Should orchestration use durable checkpoints?”, say that a customer starts a 30-minute run, a worker restarts at step 18, and they expect the same run to continue; then explain that saving progress after each step enables that behaviour and ask whether preserving the run is worth the added storage and recovery complexity.

Keep the scenario anchor compact, but never omit it. The session is complete when the whole implementation path can be explained from user action to visible result, including the important failure paths, with no consequential technical choice left implicit.
