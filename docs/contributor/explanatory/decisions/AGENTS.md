# explanatory/decisions/ — why choices were made

**Frame:** Explanatory — past reasoning.

A decision record hands over the reasoning behind a past choice: the situation, the options weighed, the condition that ruled each rejected option out, and what was chosen.
Its job is to let a future reader grasp intent without re-deriving it — and to check, before re-proposing a rejected option, whether the condition that ruled it out still holds.

## Reading rule

A decision describes the world **as it was when written**.
Read it to understand why, never to learn current state; the descriptive frame owns that.

## Alignment rule

A decision that no longer matches reality is a **non-event**.
It never claimed to describe now, so there is nothing to fix and nothing to reconcile.
Decisions are **append-only**: to change course, write a new decision that supersedes the old one; never edit the old record's body.
Supersession is triggered by a changed condition, not merely a changed preference.

For a **pointer** (a decision recorded in an external system), the same rules apply to the target; if the external record is edited in place, note that here rather than trusting it as history.

## What belongs here

The reasoning, compressed.
Don't link to the discussion that produced a choice as a stand-in for capturing it — that defers the work to the reader.
And don't describe how the project currently works in detail; that is an abstraction's job, so link to it instead.

Per the root contract, finding a decision that seems wrong or stale authorizes no edits: surface it and propose a superseding record.

Naming, template, and the supersession marker: see [`conventions.md`](conventions.md).
