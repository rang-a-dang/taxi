---
id: 0006
title: Carry the model in AGENTS.md, conventions.md, and skills, split by ownership and loading
date: 2026-07-05
---

## Context

A taxonomy that lives only in a specification is theory; an agent has to encounter the rules at the moment they apply.
Agents load context in three ways: ambient files always in context, per-directory files loaded when a directory is touched, and task-triggered procedures loaded when work matches.
The model's guidance divides the same way: how to read what's here (needed whenever reading), how artifacts are shaped and stored (needed only when writing), and how knowledge moves (needed only during that task).

## Options considered

- **A single monolithic guidance file** (one SKILLS.md-style document carrying reading rules and procedures).
  Ruled out: always loaded, it spends context on procedures that rarely apply; loaded on demand, it is too coarse to trigger precisely.
- **Storage and format detail inside each directory's contract.**
  Ruled out twice: it spends ambient reading-time context on write-time detail, and it bakes a storage substrate into the semantic rules — "supersede by editing frontmatter" breaks the moment a frame is backed by anything but files.
  It also blurs who owns what: adopters must be able to change shape without touching meaning.

## Decision

Three carriers, split by the ownership line and the loading model:

- **`AGENTS.md`** — Taxi-owned, ambient contract: one at the root, one per directory, each stating what its spot means, the reading rule, and the alignment rule, written substrate-agnostically.
- **`conventions.md`** — adopter-owned configuration, one per kind directory: naming, frontmatter, templates.
- **Skills** — task-triggered procedures for the verbs, loading only when work matches.

The dividing test between the first two: if changing it changes what an artifact *means*, it is contract and belongs in `AGENTS.md`; if it only changes how the artifact is shaped or stored, it is convention.
The ownership line lets Taxi ship contract updates without clobbering adopter configuration.
