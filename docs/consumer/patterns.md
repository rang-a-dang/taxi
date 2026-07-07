# Using Taxi in practice

These are the common workflows, done by hand.
Each directory's `AGENTS.md` states the contract and its `conventions.md` states the shape; the steps below just walk them in order.

## Adopting Taxi in your repo

1. Recreate the tree: `docs/consumer/` and `docs/contributor/` with the frame directories ([layout](reference.md#directory-layout)).
2. Copy the per-directory `AGENTS.md` and `conventions.md` files from this repository — they are project-agnostic.
3. Write your root `AGENTS.md`, starting from this repository's: keep the frame rules and operating rules, and replace the ground-truth section with where your real source lives and what an agent needs to know before changing it.
   If your repo already has a root `AGENTS.md`, merge — put the Taxi contract above your existing conventions.
4. Add the `CLAUDE.md` shims (one line, `@AGENTS.md`) beside each `AGENTS.md` if anyone on the team uses Claude Code.
5. Seed the descriptive frame first: skim your existing README, design docs, and wiki, and pull what is true *now* into one or two abstractions.
   This is the highest-value step — it gives an agent something to rely on immediately.
   Don't import documents wholesale; their value is lost if old, current, and aspirational content stays mixed.
6. Sort the rest as you touch it: rationale into decisions, roadmap into targets, standing rules into constraints, unsorted observations into the inbox.
7. If knowledge will keep living in an external system your team maintains, don't copy it — create a pointer (`external:` link) in the right frame.

Empty frames are fine.
A young project may have no decisions or plans yet; leave the directory with its `AGENTS.md` and `conventions.md`, and don't manufacture artifacts to fill it.

## A bug report arrives

1. Capture it in `contributor/inbox/` (or your external intake, if the inbox `AGENTS.md` declares one) as a raw observation with its source.
2. Triage it — decide what the item *means*:
   - It exposed a wrong mental model → update the relevant **abstraction**.
   - The project should behave differently → write a **target** (and a **plan** if the route is clear).
   - Working as intended → **dismiss** it, recording why in the artifact where that reasoning will be found again.
3. Delete the inbox item.
   Its substance now lives in the right frame.

## You finish a feature

1. Behavior changed, so update the governing **abstraction** in the same change; the descriptive frame moves with reality.
2. If the work satisfied a **target**, convert it: move the file to `descriptive/abstractions/`, add the abstraction frontmatter, and remove the **plan** that served it.
3. If you made a choice future readers will question, record a **decision** while the reasoning is fresh.

## You're starting a new direction

1. Write a **target**: the desired project, present tense, as if it already existed, with an "Out of scope" boundary.
2. If the case for it needs recording, that's a **decision**; link it rather than arguing inside the target.
3. If the property must hold forever rather than be reached once, it's a **constraint**, not a target.
4. Break the route into a **plan** linked to the target via `serves:`.
   The gap between plan and reality is the remaining work — read it by comparison, don't mark it in the file.

## An agent reads the repo cold

The root `AGENTS.md` loads first and says how to weight everything else.
From there:

- to understand **why**, read `explanatory/decisions/`;
- to learn **what is**, read `descriptive/abstractions/` and the code;
- to see **what should be**, read `normative/`;
- never infer current state from a decision, a target, or a plan.

When the agent finds a gap — an abstraction contradicting the code, a violated constraint — the contract tells it what the gap *means*, and the posture is detect, classify, surface, propose: no persisted fixes without explicit direction.

## Knowledge lives in a wiki or tracker

Create a pointer in the frame the content belongs to: a thin file with an `external:` link and a one-line note on what the source covers.
If the external content spans frames, add a pointer in each relevant frame rather than duplicating it.
If a pointer accumulates errata, promote it: pull the content into the repo and take control.
