---
id: 0008
title: The spec lives where the taxonomy says it goes, not in a SPEC.md
date: 2026-07-05
---

## Context

A framework repository usually carries a top-level SPEC.md describing itself.
But Taxi prescribes where each kind of knowledge belongs, and an authoritative description of how the system works now is, in Taxi's own terms, a descriptive abstraction.

## Options considered

- **Ship a conventional SPEC.md at the root.**
  Ruled out: it would sit outside the taxonomy the repo exists to demonstrate, weaken the claim that the structure suffices, and create a second source of truth alongside the abstraction that would have to exist anyway.

## Decision

No SPEC.md.
The authoritative model lives as the abstraction at `docs/contributor/descriptive/abstractions/taxonomy.md`, the user-facing interface lives in `docs/consumer/`, and the README is the front door that points into the structure.
The repository is thereby its own worked example: reading its `docs/` tree *is* reading a correctly organized Taxi project, and any contradiction between Taxi's docs and Taxi's rules is a visible bug.
