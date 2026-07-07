---
id: 0009
title: Bridge Claude Code with one-line CLAUDE.md shims; AGENTS.md stays canonical
date: 2026-07-05
---

## Context

Taxi's contracts live in `AGENTS.md` files, which several agents (Codex, Cursor, Gemini CLI) read natively per the agents.md convention, including nested ones.
Claude Code reads `CLAUDE.md` instead — never `AGENTS.md` — loading the root file at launch and nested ones lazily, when files in that subdirectory are read.
Its documentation offers an import syntax (`@AGENTS.md`) and notes that symlinking is an alternative.
Without a bridge, the contracts would be invisible to one of the most widely used agents.

## Options considered

- **Ship AGENTS.md only** and rely on the root contract instructing agents to read per-directory files.
  Ruled out for the root itself: with no CLAUDE.md at all, Claude Code loads nothing at launch, so even the instruction to go read the contracts never enters context.
- **Make CLAUDE.md the canonical file.**
  Ruled out: the nested-contract behavior Taxi relies on is the agents.md convention, read natively by the other agents; canonicalizing one vendor's filename would invert that and still require shims for everyone else.
- **Symlink CLAUDE.md → AGENTS.md.**
  Ruled out as the default: creating symlinks on Windows requires elevated privileges or developer mode, and a checkout is expected to work everywhere.
- **Duplicate the content into both files.**
  Ruled out: two copies of a contract drift, and a drifted contract is worse than a missing one.

## Decision

`AGENTS.md` is canonical everywhere.
Each directory that carries one also carries a one-line `CLAUDE.md` containing exactly `@AGENTS.md`, so Claude Code loads the same contract at the same moments its lazy-loading provides: root at launch, per-directory on first read there.
A shim never carries content of its own.
Because lazy loading is read-triggered, the root contract also instructs agents to read a directory's `AGENTS.md` before *writing* there — covering the case where nothing in that directory has been read yet.
