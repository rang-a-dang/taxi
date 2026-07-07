# Targets — storage conventions

Adopter-owned defaults for how targets are stored and shaped in this project.
Change them to fit your tools without violating Taxi; the contract in [`AGENTS.md`](AGENTS.md) is what's fixed.

One file per target, named `kebab-case-goal.md`.
No frontmatter: location classifies the artifact, git records its dates, and the work is tracked wherever you track work.

Write the body as you'd write an abstraction — the desired project described as if it already existed.
Don't narrate the gap ("currently X, but we want Y"); the gap is found by comparing the target against the present, not written into its prose.

```markdown
# <What the project should be>

Present-tense description of the desired state:
structure shown, invariants stated, concrete enough to check against reality.

## Out of scope

What this target does not cover. (Bounds the claim; not reasoning.)
```

**Converting a met target.**
Move the file to `../../descriptive/abstractions/` and add the abstraction frontmatter (`updated`, `covers`).
The body needs no rewrite.
