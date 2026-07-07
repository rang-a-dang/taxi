# Inbox — storage conventions

Adopter-owned defaults for how inbox items with no external home are stored here.
Change them to fit your tools without violating Taxi; the contract in [`AGENTS.md`](AGENTS.md) is what's fixed.

One file per item, named `YYYY-MM-DD-short-slug.md`.
No frontmatter: the date lives in the filename, and an item is untriaged by being present.
The body states the raw observation and its source; don't pre-judge what it becomes.

```markdown
Clicking "undo" twice in a row crashes the editor on v2.3 (macOS).
Source: user report #1423.
```
