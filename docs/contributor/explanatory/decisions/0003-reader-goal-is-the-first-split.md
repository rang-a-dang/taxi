---
id: 0003
title: Split by reader goal first; frames partition the contributor side only
date: 2026-07-05
---

## Context

The frames classify contributor knowledge cleanly, but user-facing documentation kept sitting awkwardly beside them: it has no explanatory or normative tail of its own, and forcing it into the frames explained nothing.
The model needed to say where the consumer fits, and why the frames matter to one audience and not the other.

## Options considered

- **Treat the consumer view as a subdivision of the descriptive frame** ("the present, packaged for users"), with frame as the sole primary axis.
  Ruled out: it implies the frames structure the consumer view, and they barely do — the consumer view is organized for use, not by frame.
  It also buries the split readers actually make first.
- **Place consumer documentation inside the contributor tree.**
  Ruled out: it forces a user to walk past reconciliation machinery to find out how to call a function, defeating the cognitive-load separation the layer exists for.
- **Give the consumer side frames of its own.**
  Ruled out: a frame marks an artifact's standing relative to current truth, and that mark only does work for someone who must keep artifacts and reality telling one coherent story — someone who reconciles.
  A consumer never holds an artifact against reality; they receive statements a contributor already reconciled and labeled.
  History and roadmap reach them as settled report, not as claims to classify.

## Decision

Taxi classifies along two questions, applied in order.
**Reader goal** — use or change — is the first structural split: `consumer/` and `contributor/` at the top level, so a user branches immediately and never meets the frames.
**Frame** partitions the contributor side only.
The distinction is operative versus received: frames mark standing relative to current truth, only the reconciler needs the mark, and the consumer is told rather than reconciling.
Within the consumer view Taxi is non-prescriptive, recommending an abbreviated Diátaxis (orientation / reference / patterns) as the default.
