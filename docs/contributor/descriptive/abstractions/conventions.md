# Abstractions — storage conventions

Adopter-owned defaults for how abstractions are stored and shaped in this project.
Change them to fit your tools without violating Taxi; the contract in [`AGENTS.md`](AGENTS.md) is what's fixed.

One file per coherent concept or component, named `kebab-case-topic.md`, with frontmatter:

```markdown
---
updated: YYYY-MM-DD
covers: <which part of the project this describes>
---

# <Concept>

Description of how this works now.
Present tense.
State invariants explicitly, and link to the decisions that explain why it's shaped this way.
```

**Pointers.**
A pointer uses the same filename convention but adds `external: <url>` to the frontmatter.
Its body is a one-line note on what the source covers, plus any errata — not a copy of the content.
