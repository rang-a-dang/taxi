---
id: 0004
title: Taxi states intentions; it does not enforce, track, or act
date: 2026-07-05
---

## Context

As the model was pressed on external systems and agent behavior, the language kept drifting toward process: "enforce", "verify", "status", "governed".
That vocabulary implies something *runs* — that Taxi checks placements, watches trackers, or guarantees agreement between docs and reality.
Dressed in that language, Taxi would be mistaken for a project-management or compliance system, taking on guarantees it can't keep and stepping on the team's SDLC.
The same pressure appeared on the agent side: alignment rules that say what a gap means read, to an eager agent, like permission to fix it.

## Options considered

- **Make Taxi an active checker** (lint, CI, sync).
  Ruled out: that is a tool *built on* Taxi, not Taxi; conflating them makes the taxonomy claim guarantees a set of categories cannot make.
- **Carry status fields** (`open`, `done`, `active`, progress checkboxes) on artifacts.
  Ruled out: status is execution state, and execution belongs to the team's tracker.
  Location and presence already carry lifecycle — an inbox item is untriaged by being there, a met target converts, a finished plan is removed — so a status field is either redundant or a lie waiting to happen.
- **Let alignment rules authorize autonomous fixes.**
  Ruled out: an agent that "re-syncs" documentation or code unprompted is performing persisted writes on the strength of a classification, and a misclassification then propagates silently.

## Decision

Taxi is a taxonomy: it states where knowledge belongs and what a gap means, and nothing more.
It has no runtime, no checks, no promises; a misfiled artifact is wrong whether or not anyone notices, and Taxi's value is that the misfiling is *findable*.
Two rules hold the line:

- **No status fields.**
  The one relationship marker is `superseded-by:` on decisions, which links records rather than tracking progress.
- **No unprompted persisted action.**
  The agent posture is detect, classify, surface, propose; persisted writes require explicit user direction.

Word choices follow: "should align", "tension", "intended relationship" — never "enforce" or "guarantee".
