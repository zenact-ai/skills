Quickstart:

```bash
npx skills add mattpocock/skills --skill=product-grill-me
```

```bash
npx skills update product-grill-me
```

[Source](https://github.com/mattpocock/skills/tree/main/skills/engineering/product-grill-me)

## What it does

`product-grill-me` frames every decision in the concrete product scenario it affects. It establishes the user, their goal, the flow, and the product promise first, then asks only the decisions whose consequences escape the codebase.

Its defining filter is simple: would a user, support ticket, demo, bill, or SLA reveal a difference? If yes, the user decides. If not, the agent treats it as an implementation call, investigates or resolves it, and records the call for review at the end.

## When to reach for it

You invoke this by typing `/product-grill-me` — the agent won't reach for it on its own.

Reach for it when a technical plan contains many possible questions but you only want human attention spent on choices that change the product experience or its promises. For a general plan that does not need the product-decision filter, use [grill-me](https://aihero.dev/skills-grill-me); when the session must also build a glossary and record durable decisions, use [grill-with-docs](https://aihero.dev/skills-grill-with-docs).

## The noticeable-difference test

The session works **from the product inward**. Every candidate question is classified before it reaches the user. Product decisions are ordered by user stakes, beginning where the flow's promises are most at risk rather than where the implementation is most technically interesting.

Each question then states the scenario, problem, behavioural options, and recommendation in ordinary language. Technical mechanisms appear only far enough to explain how each option produces the visible outcome.

## The closing walkthrough

The session ends by replaying the resolved user journey from start to finish. Implementation calls the agent made independently follow as a one-line log, giving the user a final chance to veto anything that should have been treated as a product decision.

## It's working if

- Every question names the user-visible scenario and consequence.
- The most consequential product decisions are asked first.
- Internal choices that nobody outside the codebase would notice do not consume the interview.
- Technical terms explain a mechanism; they never replace the problem statement.
- The closing walkthrough exposes every resolved product decision and independently made implementation call.

## Where it fits

`product-grill-me` is a reach-for-it-anytime standalone for the point where product intent and technical design need to meet. It uses the same one-question-at-a-time discipline as [grilling](https://aihero.dev/skills-grilling), and its settled decisions can feed [to-spec](https://aihero.dev/skills-to-spec) without another interview. When you're unsure which flow fits, [ask-matt](https://aihero.dev/skills-ask-matt) routes you.
