# Taxi, oriented

## What it is

Taxi is a way to organize a project's knowledge so that a reader with no accumulated context — an AI agent starting its session from zero, or a human opening an unfamiliar repo — can tell **what kind of claim it's reading**.
Instead of one undifferentiated pile of design docs, notes, and wikis, Taxi anchors every artifact to a *frame*: does it explain a past choice, describe current reality, or state what should be true?
The frame is carried by where the artifact lives.

Concretely, Taxi is a directory layout plus a set of `AGENTS.md` contracts.
No runtime, no service, no database, no new tooling.

## What it's for

- Giving AI agents reliable footing in a project: unambiguous signals about what to rely on, what is historical reasoning, and what is intent.
- Keeping documentation honest by giving each claim exactly one place to be, with a stated meaning for any gap between the claim and reality.
- Separating the knowledge a *user* needs from the knowledge a *builder* needs, so neither wades through the other.

## What it's *not* for

- It is **not** a documentation generator or wiki engine. It doesn't write your docs; it says where each kind belongs and how to treat it.
- It is **not** a process methodology or a ticketing system. Nothing in Taxi carries status, assignees, or progress; the inbox is a triage surface, not a backlog.
- It does **not** enforce anything. Taxi states where knowledge belongs and what a discrepancy *means*; nothing polices the rules, and anything requiring a guaranteed process belongs to your team's own workflow.
- It is **not** a replacement for good prose. A badly written description is still bad; Taxi just makes sure nobody mistakes it for history or intent.
- It does **not** require special tooling. Any repo that can hold Markdown files can use Taxi.

## Next

[`reference.md`](reference.md) for the precise interface, or [`patterns.md`](patterns.md) for how to use it day to day.
