# Constraints — storage conventions

Adopter-owned defaults for how constraints are stored and shaped in this project.
Change them to fit your tools without violating Taxi; the contract in [`AGENTS.md`](AGENTS.md) is what's fixed.

One file per constraint, named `kebab-case-rule.md`.
No frontmatter: location classifies the artifact, and a constraint has no lifecycle to mark — it stands until deliberately retired.

State the property universally: something that must hold for every present and future state, checkable against reality.

```markdown
# <The property that must hold>

The rule, stated so a violation is recognizable:
what must be true of every state of the project, and what counts as breaking it.

## Scope

Where the rule applies, and any deliberate exclusions. (Bounds the claim; not reasoning.)
```

The case *for* the rule is explanatory: record it as a decision and link it, don't argue it here.
