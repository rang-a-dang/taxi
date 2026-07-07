---
id: 0001
title: Classify artifacts by frame — the kind of claim each makes
date: 2026-07-05
---

## Context

Project documentation freely mixes what was true, what is true, what should become true, and what was rejected.
A human unmixes this from accumulated context; an AI agent starts every session without that context and guesses.
Taxi needed a primary classification axis that tells any reader how to take a claim, and a name for that axis that reliably directs sorting.
Earlier iterations tried three names in sequence — temporal labels, "epistemic status", and "purpose" — before settling.

## Options considered

- **Organize by topic** ("auth", "billing").
  Ruled out: topic says nothing about how much to rely on a statement, which is exactly the ambiguity to remove.
- **Organize by document type** ("design doc", "runbook").
  Ruled out: document types correlate weakly with the kind of claim — a "design doc" may describe a shipped system or a rejected one.
- **Temporal labels (Past / Present / Future) as the axis.**
  Ruled out: the metaphor took over.
  Readers — AI especially — sorted by literal chronology, filing an artifact that originated in a past event as "past" even when it functionally described the present, and expected the tree to behave like a changelog.
- **"Epistemic status" as the axis name.**
  Ruled out: epistemic status only covers claims about what is *true*, and one member of the set is a claim about what is *intended* — not a knowledge claim at all.
  Standing requirement extracted from this failure: the axis word must accommodate a member that isn't a truth-claim.
- **"Purpose" as the axis name.**
  Ruled out three ways: it collides with the goal-like member (a goal *is* a purpose), it is vague (everything has a purpose), and it names the author's intent when the classification is really about how the *reader* should treat the thing.

## Decision

The axis is the **frame**, glossed in prose as "the kind of claim it makes".
One word does both jobs — it names the axis and the slot — and it presupposes no truth, so it clears the non-truth-claim requirement.
The reading-frame metaphor is also the thesis in miniature: same letters, shift the frame, different meaning.
Second choice, if "frame" ever needs replacing: **stance**.
