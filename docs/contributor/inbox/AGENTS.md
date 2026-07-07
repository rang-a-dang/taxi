# inbox/ — raw input awaiting triage

**Frame:** none yet.

This is a staging area, not a record.
Items arrive as raw observations: a bug report, a metric, a complaint, an idea, an undecided proposal.
Unlike everything else in the tree, inbox items are **self-describing** — "in v2.3, clicking undo twice crashes" already says what was observed and when — so they don't need a frame to be understood.
What they need is **triage**.

## Reading rule

An inbox item makes no maintained claim.
Don't rely on it as fact, goal, or history; don't act on it as if it were framed.

## Alignment rule

Not applicable: an item here asserts nothing about the project, so there is no gap to interpret.
The only thing an inbox item can be is *pending*, and it is pending by being here.

## The inbox is a role; this directory is its default backing store

The inbox is the intake boundary for untriaged input.
If the project already triages somewhere else — a tracker, an issue queue — that system *is* the inbox; declare it below and triage against it in place rather than mirroring items here.

<!-- Adopter: list any external systems that serve as this project's inbox.
     If none are listed, this directory is the only inbox. -->

## Triage and clear

Triage **separates** a mixed item into framed atoms, or dismisses it:

- It revealed a wrong mental model → update an **abstraction**.
- The project should change → a **target** (and maybe a **plan**).
- It prompted a choice → record a **decision**.
- Working as intended or out of scope → **dismiss**, recording why where it will be found (usually a note in the relevant artifact).

A triaged item leaves the inbox: its substance moves to the destination frame and the file is deleted.
An inbox that fills up is a smell — observations are being hoarded instead of metabolized.

Naming and shape for items stored here: see [`conventions.md`](conventions.md).
