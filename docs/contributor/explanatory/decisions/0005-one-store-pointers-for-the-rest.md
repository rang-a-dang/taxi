---
id: 0005
title: Enforce one local store; external knowledge enters through pointers
date: 2026-07-05
---

## Context

Most projects keep knowledge in many places: wikis, ADR tools, trackers, knowledge bases.
If Taxi classified only in-repo files, most of a project's knowledge would be invisible to an agent, and invisible means untrusted.
Taxi had to say how external knowledge participates without becoming a sync engine, and how artifacts are stored without every future procedure carrying a storage abstraction.

## Options considered

- **Swappable storage backends** (each frame configurable to a wiki, a database, an MCP).
  Ruled out: every skill and contract would have to carry a storage driver in prose, and prose drivers are fragile; the payoff doesn't cover the cost.
- **Mirror external content into the repo.**
  Ruled out: duplication invites drift, and keeping mirrors current is a sync process — exactly what Taxi must not be.
- **Trust tiers** ("governed" vs "indexed" content).
  Ruled out: those labels imply a process acted on the document, and likelihood-of-correctness is the wrong axis — Taxi never claims anything is probably right.
  What actually differs between local and external content is what you can *do* about a gap.

## Decision

Taxi enforces a single backing store: local Markdown in the frame directories, shaped by each kind's `conventions.md`.
Pluggability comes from the **entry type**, not the backend: a frame entry is an **artifact** (content in the repo) or a **pointer** (a thin local entry with an `external:` link to frame-grade content elsewhere).
The distinction is **control, not trust** — an artifact you fix; a pointer's gap you surface to whoever owns the target, and a pointer that accumulates errata gets promoted to an artifact.
Pointers reference only already-metabolized, frame-grade content; raw input still goes through triage.
The local skeleton of entries — even if it is all pointers — doubles as the always-available index of what the project knows and where.
As a guard against lock-in, procedures speak to a minimal item interface (read, list, create, supersede, mark-tension) rather than to file mechanics.
