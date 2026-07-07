# descriptive/abstractions/ — what is true now

**Frame:** Descriptive — present truth.

An abstraction is a conceptual description of the project as it exists **right now**: the components, what they own, how the pieces actually fit and flow.
It is a compression of ground truth at a chosen level of detail — faithful but lossy — so a reader can build an accurate mental model without reading everything.

## Reading rule

Rely on an abstraction as current fact.
It is neutral: it reports, it never judges, and it never carries aspiration.

## Alignment rule

An abstraction that disagrees with ground truth is a **contradiction**, and the abstraction is the false side: ground truth wins, so the abstraction is stale and should be re-synced.
Whether ground truth itself is *wrong* is a normative question — decided by a constraint or target, never by a descriptive doc.
Before treating a disagreement as staleness, rule out a misfiling (the content belongs in another frame) or frame bleed (one artifact mixing descriptive and normative claims, which needs splitting, not syncing).

For a **pointer** (an `external:` link to a current-state description elsewhere), you don't control the target, so record and surface the tension — an erratum note here, a request to the owner — instead of editing.
A pointer that accumulates errata should be promoted to an in-repo abstraction.

Per the root contract, re-syncing is proposed, not performed unprompted.

## What belongs here

- Present-tense, checkable claims about the current project.
- **Not aspiration**: "should" content is a target or constraint.
- **Not rationale**: why a mechanism was chosen is a decision; link it.
  The change-test settles borderline sentences: if changing the project would force the sentence to change, it's descriptive; if it would stay true as a record of the past, it's explanatory.
- **Not properties a constraint owns**: the descriptive frame must not mirror a constraint, or the rule and the report blur.

Cross-link generously: an abstraction that points at its originating decisions and the ground truth it compresses is far more useful than one floating alone.

Naming and shape: see [`conventions.md`](conventions.md).
