# consumer/ — using the project

**Audience:** people and agents who *use* the project.

Everything here is intended to be **present truth, packaged for a user**.

The default layout is an abbreviated [Diátaxis](https://diataxis.fr/) in three files:

- **`orientation.md`** — What is this? What is it for? What is it *not* for?
- **`reference.md`** — What exactly does it expose? The precise interface.
- **`patterns.md`** — How is it used in practice? Some examples.

This is Diátaxis without the tutorial quadrant.
Tutorials serve human learning goals — confidence, a sense of achievement, the feeling of doing — that don't apply to an AI reader, and the how-to material they share with guides folds into `patterns.md`.
This organization is a **recommendation, not a rule**.
Taxi classifies knowledge as consumer-facing and then steps back; full Diátaxis or another organization is fine as long as the rules below hold.
If you update the structure, e.g., by making subdirectories instead of Markdown files, remember to update this file.

## Rules for writing here

- If **using** the project requires a fact, surface that fact here. Don't send the user to an internal `contributor/` document.
- **Stay in sync.** When the project changes, update the `consumer/` documentation as needed.
