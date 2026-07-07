# Plans — storage conventions

Adopter-owned defaults for how plans are stored and shaped in this project.
Change them to fit your tools without violating Taxi; the contract in [`AGENTS.md`](AGENTS.md) is what's fixed.

One file per plan, named `kebab-case-plan.md`, linked to the target or constraint it serves:

```markdown
---
serves: <slug of the target in ../targets/ or constraint in ../constraints/>
---

# Plan: <name>

## Approach

The strategy in a paragraph — the shape of the route.

## Steps

The route in order.
Steps describe the work, not who is doing it or how far along it is.

## Risks / unknowns

What could invalidate the approach.
```

No status and no checkboxes: a plan records the route, and progress is read by comparing it against reality, not marked in the file.
