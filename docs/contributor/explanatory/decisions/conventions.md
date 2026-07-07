# Decisions — storage conventions

Adopter-owned defaults for how decisions are stored and shaped in this project.
Change them to fit your tools — one file per decision, an ADR tool, a wiki — without violating Taxi; the contract in [`AGENTS.md`](AGENTS.md) is what's fixed.

One file per decision, named `NNNN-short-slug.md` with a zero-padded sequence number.
Use this template:

```markdown
---
id: NNNN
title: <one line, imperative or declarative>
date: YYYY-MM-DD
---

## Context

The situation that forced a choice.

## Options considered

Each option that was seriously weighed.
For every option not taken, state the specific, checkable condition that ruled it out —
a falsifiable claim about reality, not a vague preference.

## Decision

What was chosen, and what follows from choosing it.
```

The ruled-out options and their conditions are the content that carries the record; keep them sharp.

**Superseding.**
To reverse a decision, write a new record and add `superseded-by: NNNN` to the old file's frontmatter.
Leave the old body untouched.
