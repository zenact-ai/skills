Quickstart:

```bash
npx skills add mattpocock/skills --skill=product-grill-me
```

```bash
npx skills update product-grill-me
```

[Source](https://github.com/mattpocock/skills/tree/main/skills/engineering/product-grill-me)

## What it does

`product-grill-me` takes one concrete product scenario and grills how the system implements it end to end. It starts with the user action and visible outcome, then walks through the entry point, components, data, state, asynchronous work, failures, recovery, and the result returned to the product.

The product scenario stays fixed as the spine while most of the session happens at the technical implementation level. It never presents a technical decision in isolation: each question supplies the product, technical, prioritisation, and existing-pattern context needed to judge the choice.

## When to reach for it

You invoke this by typing `/product-grill-me` — the agent won't reach for it on its own.

Reach for it when you need to work out exactly how a feature, flow, or failure scenario should travel through the system, and you want the technical design challenged one step at a time without losing sight of what the customer experiences. For a general plan that does not need an implementation walkthrough, use [grill-me](https://aihero.dev/skills-grill-me); when the session must also build a glossary and record durable decisions, use [grill-with-docs](https://aihero.dev/skills-grill-with-docs).

## The context around the choice

The session works **from the product inward**. Product context explains who needs the behaviour and why. Technical context locates the decision in the implementation path. Prioritisation context states what matters now and what can wait. Patterns context shows how the closest analogous case is already handled in the codebase.

Those contexts are evidence, not ceremony. The agent pulls them from the actual product material and codebase, keeps only what changes the choice, and explains when following an existing convention is safer than inventing a new path—or when the product and priority demands justify breaking from it.

## It's working if

- You can trace the complete implementation from the user's action to the visible result.
- Every important state transition, dependency, and failure path has an explicit handling strategy.
- Every recommendation accounts for the product outcome, technical constraints, current priority, and existing code conventions.
- Technical terms explain a mechanism; they never replace the problem statement.
- Each question resolves one technical choice on the scenario's implementation path.

## Where it fits

`product-grill-me` is a reach-for-it-anytime standalone for the point where product intent and technical design need to meet. It uses the same one-question-at-a-time discipline as [grilling](https://aihero.dev/skills-grilling), and its settled decisions can feed [to-spec](https://aihero.dev/skills-to-spec) without another interview. When you're unsure which flow fits, [ask-matt](https://aihero.dev/skills-ask-matt) routes you.
