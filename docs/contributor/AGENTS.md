# contributor/ — changing the project

Everything here is for people and agents **changing** the project.
It is organized by **frame** — the kind of claim each artifact makes.

```
inbox/                       raw input awaiting triage (not a frame)
explanatory/decisions/       why choices were made — append-only
descriptive/abstractions/    what is true now — must agree with code
normative/targets/           what should become true — once true, move necessary content to descriptive/abstractions/
normative/constraints/       what must stay true — persistent, e.g., architectural guidelines
normative/plans/             the route from here to there — once complete, can be deleted or archived
```

**The flow of knowledge:** something is observed → it lands in `inbox/` → triage separates it into framed artifacts.
Do not write into a frame without asking what kind of claim the content makes.
Each kind directory has its own `AGENTS.md` (the contract) and `conventions.md` (naming and shape); read both before creating anything there.

Consumers must never need to read anything in here.
A fact a *user* needs belongs in [`../consumer/`](../consumer/).
