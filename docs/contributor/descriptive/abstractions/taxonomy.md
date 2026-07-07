# The Taxi taxonomy

This is the authoritative description of what Taxi *is*: the model that the directory scaffold, the `AGENTS.md` contracts, and the `conventions.md` defaults implement.
If the shipped surface disagrees with this document, that is a contradiction in the descriptive frame; resolve it, don't tolerate it.

## The core claim

A project artifact's meaning is not determined by its words alone.
"Sessions are stored in Redis" can be how the system works now, how it worked before a migration, something planned, or an approach that was floated and rejected — and the sentence itself doesn't say which.
A human working on the project supplies the missing context from accumulated experience; an AI agent starts every session without it, picks a reading, and runs.

Taxi anchors every artifact to a **frame** — the kind of claim it makes — and lets *where the artifact lives* carry the frame.
The same words mean different things in different places, so the place is made to say how to read the words.
No prose label to write, lose, or let go stale: the frame is structural.

## The frames

The organizing question is: **what does a gap between the artifact and reality mean?**
There are exactly three answers, and the set is closed:

| Frame | The claim | A gap is… | Resolution |
|-------|-----------|-----------|------------|
| **Explanatory** | past reasoning | a **non-event** | none — it never claimed to describe now |
| **Descriptive** | present truth | a **contradiction** | re-sync the artifact; reality wins |
| **Normative** | not-yet truth | a **distance** | do the work, or re-aim deliberately |

The closure argument: a persisted claim either isn't about the present (explanatory), claims the present matches it (descriptive), or claims the present *should* match it (normative).
A would-be fourth frame is always a topic that cross-cuts these, a kind within one of them, or raw input for the inbox.
Do not add a fourth frame.

### Explanatory — the why

Explanatory artifacts hand over the reasoning behind how things got this way: intent, trade-offs, and especially what was ruled out, so a reader doesn't re-tread dead ends or misread the present.

- A mismatch with reality is a non-event; nothing needs fixing.
- Not recoverable from the project itself: the why and the rejected options live nowhere else.
- Append-only: to revise, supersede with a new artifact; never edit the old one.

Its kind in this repo is the **decision** (shape: Context / Options considered / Decision).
The value concentrates in the ruled-out options and the checkable condition that ruled each out — that is what a future reader must re-check before re-proposing one.
The same shape applied to an event rather than a choice — a post-mortem — is the other explanatory kind; this repo doesn't carry any yet.

### Descriptive — what is

Descriptive artifacts compress ground truth so a reader can build an accurate mental model without reading everything.

- A mismatch is a contradiction, and the artifact is the false side: reality is ground truth, so the artifact is stale and gets re-synced.
- Whether reality itself is *wrong* is a normative question; the descriptive frame is mechanical and judgment-free.
- Recoverable from the project: faithful but lossy — everything in it is true of the project, but it doesn't depict everything.
- Neutral: it reports, never judges, and never mirrors a property a constraint already owns.

Its kind is the **abstraction**: the components, what they own, how things actually fit and flow, at a chosen level of detail.
There is no contributor "reference" kind — a precise interface is either recoverable from the project or, as a contract, normative.
The user-facing reference is a consumer artifact, not part of this frame.

### Normative — what should be

Normative artifacts state where the project is headed and what it must satisfy, kept apart from what is true so intent is never mistaken for fact.

- A mismatch is a distance — legitimate, not a defect; the distance is the work.
- This is the only frame where judgment chooses *what changes*: close the gap by building, or change the norm deliberately, recorded with a decision — never by silently editing the norm to match reality.
- Not recoverable from the project: intent isn't in the artifact's absence; the project can satisfy or violate a norm but can't tell you it exists.
- Leads the project: it has authority over what the project should become.

Three kinds:

- **Target** — existential and one-shot: a specific desired state that isn't true yet.
  When met, it **converts**: it is discharged and the new reality is recorded descriptively (the present-tense body usually carries over unchanged).
- **Constraint** — universal and standing: a property that must hold across all present and future states.
  It **never converts**; even fully satisfied it remains, governing the space of allowed states.
  A violated constraint is a distance with teeth: fix the project or change the rule via a decision.
- **Plan** — the route from the present to a target, or the standing process that keeps a constraint satisfied.
  It records the route, never the progress along it; when the route has been walked, the plan is removed.

## The inbox — not a frame

Raw input — a bug report, an idea, a metric, an undecided proposal — arrives unframed and **self-describing**: it already states what was observed and when, so it needs no frame to be understood.
What it needs is **triage**: separating the mixed item into framed atoms, or dismissing it.
The inbox is a staging area, not a record; it is emptied, not hoarded.

The inbox is also a *role*, not only a directory.
If a team already triages in a tracker, that system is the inbox; the directory's contract declares where intake lives, and triage runs against it in place rather than mirroring items into the repo.

A proposal still under debate stays whole in the inbox: deciding is what makes it splittable.
Once decided, it separates — a yes becomes a target, a plan, maybe constraints, plus a decision for the why; a no becomes a single decision recording what was rejected and why.

## Two classifications: reader goal, then frame

Taxi classifies along two questions.
**Reader goal** — use the project, or change it — is who the knowledge is for, and it is the first structural split: `consumer/` vs `contributor/`.
**Frame** — explanatory, descriptive, normative — is what an artifact means, and it partitions the contributor side only.

The frames are a contributor concern because a frame marks an artifact's **standing relative to what is true now**, and that mark only does work for someone who must keep the artifacts and the project telling one coherent story — someone who *reconciles*.
The consumer never holds an artifact against reality.
They receive statements already reconciled and labeled by a contributor: history as changelog, roadmap as announcement, both met as settled report.

> Frames mark each artifact's standing relative to current truth.
> Only the reconciler needs that mark.
> The consumer is told; they never reconcile.

So the frames are inert in `consumer/`, and the consumer view is organized for use instead.
The recommended default is an abbreviated [Diátaxis](https://diataxis.fr/): **orientation** (what it is, is for, isn't for), **reference** (the precise interface), and **patterns** (how it's used).
The tutorial quadrant is dropped: tutorials serve human learning goals — confidence, a sense of achievement, the feeling of doing — that don't apply to an AI reader, and their how-to substance folds into patterns.
The triple is a default, not a rule; within a view, Taxi is non-prescriptive.
Maintaining the consumer view remains contributor work: the tree is read by users and written by contributors.

## Storage: one shape, with a pointer escape hatch

Taxi enforces a single backing store: local Markdown files in the frame directories, one file per item, shaped by each kind's `conventions.md`.
Swappable backends were rejected — every procedure would have to carry a storage driver in prose — so pluggability comes from the **entry type** instead:

- An **artifact** holds its content in the repo.
- A **pointer** is a thin local entry with an `external:` link to frame-grade content that lives elsewhere (a wiki, an ADR tool, a tracker).

The difference is **control, not trust**.
Both make the same kind of claim and carry the same gap-meaning; they differ in what you can *do* when a gap appears.
An artifact you fix; a pointer's target belongs to someone else, so you surface the tension — an erratum note, a request to the owner — and a pointer that accumulates errata gets promoted to an artifact.

Point only at frame-grade content: knowledge that is already metabolized and merely lives elsewhere.
Raw input is not frame-grade; it goes through triage.
Uncontrolled content that spans frames is pointed at from each relevant frame with a short note, never duplicated.

Even a project whose knowledge lives mostly elsewhere keeps the local skeleton of pointers.
That skeleton is the always-available index of what the project knows and where — a feature, not a tax.

Documentation compresses; it does not defer.
A link to "the discussion that produced this" pushes the work of deciding what mattered onto every future reader; the only legitimate outbound link is a pointer to already-compressed content.

## The three carriers

The model reaches an agent through three carriers, split by ownership and by when each loads:

- **`AGENTS.md`** — Taxi-owned, fixed, ambient.
  One at the repo root (always in context) and one per directory (loaded when that directory is touched).
  Each states what its spot means, the **reading rule**, and the **alignment rule** — kept substrate-agnostic, so it never assumes how artifacts are shaped or stored.
- **`conventions.md`** — adopter-owned configuration, one per kind directory.
  Naming, frontmatter, templates: everything malleable about shape and storage.
  The dividing test: if changing it would change what an artifact *means*, it is contract and belongs in `AGENTS.md`; if it only changes how the artifact is shaped or stored, it is convention.
  The ownership line is what lets Taxi ship contract updates without clobbering adopter configuration.
- **Skills** — task-triggered procedures, planned but not yet shipped: the verbs (triage, record a decision, reconcile, adopt) that act on the store.
  They load only when a task matches, and they will speak to a minimal item interface — read, list, create, supersede, mark-tension — rather than to storage details, so pointers and future shapes don't break them.

Some agents read `AGENTS.md` natively; Claude Code reads `CLAUDE.md` instead, so each directory carries a one-line `CLAUDE.md` shim containing `@AGENTS.md`.
The `AGENTS.md` is always the canonical file; a shim never carries content of its own.

## Taxi states intentions; it does not enforce them

Taxi is a taxonomy, like the categories on a shelf: it says where things belong and what their placement means.
Nothing stops someone filing a spatula under clothing, and nothing in Taxi reaches into the drawer to check.
It has no runtime; it verifies nothing, syncs nothing, and guarantees nothing.
"Should align" is a stated invariant, not a performed check; a misfiled artifact is wrong whether or not anyone notices.
Anything that needs an active, guaranteed process belongs to the team's SDLC, which Taxi must not assume or replace.

Two consequences hold this line:

- **No status fields.**
  Presence and location carry lifecycle: an inbox item is untriaged by being there, a met target converts, a finished plan is removed.
  The one relationship marker is `superseded-by:` on decisions, which links records; it does not track progress.
- **No unprompted persisted action.**
  An alignment rule says what a gap *means* and what would close it; it never authorizes an agent to close it on its own.
  The default posture is detect, classify, surface, propose; persisted writes require explicit user direction.
