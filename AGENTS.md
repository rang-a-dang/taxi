# AGENTS.md

This repository is organized with **Taxi**, an artifact taxonomy that fixes how each piece of project knowledge should be read.
Read this file before acting on anything in the repo.

If you only remember one thing: **the same words mean different things in different places.**
"Sessions are stored in Redis" is context for a past choice in a decision, a fact to rely on in an abstraction, and a goal to work toward in a target.
The location carries the frame; check where you are before acting on what you read.

## The map

```
docs/
  consumer/                    how to USE the project (present truth, packaged for users)
    orientation.md  reference.md  patterns.md
  contributor/                 how to BUILD the project
    inbox/                       raw input awaiting triage — clear it, don't hoard it
    explanatory/decisions/       why choices were made (append-only)
    descriptive/abstractions/    what is true now (must agree with ground truth)
    normative/targets/           what should become true (one-shot)
    normative/constraints/       what must stay true (standing)
    normative/plans/             how to close a gap (routes)
```

## The frames

Every contributor artifact lives in exactly one of three frames, and the set is closed.
A frame answers one question: what does a gap between the artifact and reality mean?

- **Explanatory** — past reasoning.
  A gap is a **non-event**: the artifact never claimed to describe now.
  Read it for the why; never infer current state from it.
  Append-only: supersede, never edit.
- **Descriptive** — present truth.
  A gap is a **contradiction**, and the artifact is the false side: ground truth wins, so the artifact is stale and should be re-synced.
  Whether ground truth itself is wrong is a normative question, never settled here.
- **Normative** — what should be true.
  A gap is a **distance**: legitimate, and it is the work.
  Never read a normative artifact as current state.
  Close the gap by building, or change the norm deliberately and record why — never by silently editing the norm to match reality.

The **inbox** is not a frame: raw, self-describing input awaiting triage.

## Ground truth in this repo

Taxi is a taxonomy, so this repository has no source code.
What plays the role of code is its shipped surface: the README, the `AGENTS.md` contracts, and the per-kind `conventions.md` defaults.
The authoritative model is [`docs/contributor/descriptive/abstractions/taxonomy.md`](docs/contributor/descriptive/abstractions/taxonomy.md); if the shipped surface disagrees with it, that is a contradiction to resolve.

## Artifacts and pointers

A frame entry is either an **artifact** (content in this repo) or a **pointer** (a thin entry with an `external:` link to frame-grade content elsewhere).
The difference is **control, not trust**: an artifact you can fix directly; for a pointer, you don't own the target, so surface the tension instead of resolving it unilaterally.

## Operating rules

1. **Read a directory's `AGENTS.md` before writing there.**
   The per-directory contracts load only when their files are read, so fetch the contract explicitly before creating anything.
2. **Place by frame, not by topic.**
   Ask what kind of claim the content makes, then put it where that claim belongs.
3. **Keep the descriptive frame consistent.**
   When the shipped surface changes, update the affected abstraction in the same change.
4. **Never edit history.**
   A reversed decision gets a new record that supersedes the old one.
5. **Keep consumer and contributor knowledge separate.**
   A consumer must never need `docs/contributor/` to use the project.
6. **No unprompted persisted action.**
   When you find a gap: detect, classify, surface, propose.
   Persisted edits to code or docs require explicit user direction.
7. **No status fields.**
   Presence and location carry lifecycle: an inbox item is untriaged by being there, a finished plan is removed, a met target converts to the descriptive frame.
