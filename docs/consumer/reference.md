# Taxi reference

## The frames

Every contributor artifact lives in exactly one of three frames, and the set is closed.
A frame answers one question — what does a gap between the artifact and reality mean?

| Frame | The claim | A gap is… | Resolution |
|-------|-----------|-----------|------------|
| **Explanatory** | past reasoning | a non-event | none; it never claimed to describe now |
| **Descriptive** | present truth | a contradiction | re-sync the artifact; reality wins |
| **Normative** | not-yet truth | a distance | do the work, or re-aim deliberately |

## The kinds

Kinds are content shapes within a frame; they share their frame's gap-meaning.

| Kind | Frame | Question answered | Lives in |
|------|-------|-------------------|----------|
| Decision | Explanatory | Why is the project the way it is? | `contributor/explanatory/decisions/` |
| Abstraction | Descriptive | What is the project, conceptually? | `contributor/descriptive/abstractions/` |
| Target | Normative | What should the project become? | `contributor/normative/targets/` |
| Constraint | Normative | What must stay true of it? | `contributor/normative/constraints/` |
| Plan | Normative | How do we get there? | `contributor/normative/plans/` |

Target vs constraint: "if satisfied, is it done?" — yes for a target (it converts to an abstraction when met), no for a constraint (it stands, governing all future states).

## The inbox (not a frame)

`contributor/inbox/` holds raw, self-describing input — bug reports, ideas, metrics, undecided proposals — awaiting **triage**, which separates each item into framed artifacts or dismisses it.
The inbox is a *role*, not only a directory: if your team triages in an external tracker, that system is the inbox, declared in the directory's `AGENTS.md`, and triage runs against it in place.

## Entry types: artifacts and pointers

A frame entry is either an **artifact** (content in the repo) or a **pointer** (a thin entry whose frontmatter carries `external: <url>` to frame-grade content elsewhere).
The difference is **control, not trust**: an artifact you can fix; a pointer's gap you surface to whoever owns the target.
Point only at already-metabolized, frame-grade content; raw input goes through triage.
A pointer may carry an erratum when its source is believed wrong; heavy annotation is the signal to promote it to an artifact.

## Directory layout

```
AGENTS.md                      root contract, always in context (CLAUDE.md shim beside it)
docs/
  consumer/                    for people USING the project
    orientation.md  reference.md  patterns.md
  contributor/                 for people BUILDING it
    inbox/                       raw input awaiting triage
    explanatory/decisions/       why choices were made (append-only)
    descriptive/abstractions/    what is true now
    normative/targets/           what should become true
    normative/constraints/       what must stay true
    normative/plans/             how to get there
```

Every documentation directory carries an `AGENTS.md` stating its contract; every kind directory adds a `conventions.md` with the storage defaults.

## The carriers

- **`AGENTS.md`** — Taxi's fixed contract: what each spot means, the reading rule, the alignment rule.
  You don't edit these; updates come from Taxi.
- **`conventions.md`** — yours: filenames, frontmatter, templates.
  Change them to fit your tools without violating the taxonomy.
- **Skills** — task-triggered procedures for the recurring verbs.
  Taxi ships none today; the contracts and conventions are the whole current interface.

## Making Taxi legible to your agent

Codex, Cursor, and Gemini CLI read `AGENTS.md` natively, including the nested ones.
Claude Code reads `CLAUDE.md` instead, so every directory that carries an `AGENTS.md` also carries a one-line `CLAUDE.md` containing exactly `@AGENTS.md`.
Claude Code then loads the root contract at launch and each directory's contract when it first reads files there.
The `AGENTS.md` is always canonical; a shim never carries content of its own.
Because per-directory contracts load on *read*, the root contract instructs agents to read a directory's `AGENTS.md` before writing there.

## Naming defaults

Set by each kind's `conventions.md`; these are the shipped defaults.

| Kind | Filename |
|------|----------|
| Inbox item | `YYYY-MM-DD-short-slug.md` |
| Decision | `NNNN-short-slug.md` (zero-padded sequence) |
| Abstraction | `kebab-case-topic.md` |
| Target | `kebab-case-goal.md` |
| Constraint | `kebab-case-rule.md` |
| Plan | `kebab-case-plan.md` |

Frontmatter is minimal: an artifact's frame comes from its location, never from frontmatter.
Decisions carry `id`, `title`, `date` (and `superseded-by` once superseded); abstractions carry `updated` and `covers`; plans carry `serves`; pointers add `external`.
Targets, constraints, and inbox items carry none.

## Edge cases

- **A fact is both current and aspirational.** Split it: the true-today part is an abstraction; the should-be part is a target.
- **A decision was reversed.** Never edit it; write a new decision and mark the old one `superseded-by: NNNN`.
- **Where does a roadmap go?** It is a set of targets, not a consumer doc.
- **Where does status live?** Nowhere.
  Presence and location carry lifecycle: an inbox item is untriaged by being there, a met target converts to an abstraction, a finished plan is removed.
- **Code has no describing abstraction.** Either the abstraction is missing (write it) or the code is incidental enough not to need one; don't invent ceremony.
- **A rule is fully satisfied.** It remains a constraint; satisfaction doesn't convert it, and the descriptive frame doesn't restate it.
