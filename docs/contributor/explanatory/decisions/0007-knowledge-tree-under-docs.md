---
id: 0007
title: Put the knowledge tree under docs/, with the root contract at the repo root
date: 2026-07-05
---

## Context

Taxi's categories are directories, and they have to live somewhere in an adopting repository.
One constraint pulls against tidiness: the root contract must be *always* in context, and agents grant that guarantee only to files at the repository root.

## Options considered

- **Install the frame directories at the repository root.**
  Ruled out: it crowds a real project's root with framework directories and competes with whatever top-level layout the project already has.
  Prose knowledge already has a conventional home, and it isn't the root.
- **Move the root contract under `docs/` with everything else.**
  Ruled out: a contract in a subdirectory loads only when that subdirectory is touched, forfeiting the always-in-context guarantee the ambient rules depend on.
- **Make the location configurable per project.**
  Ruled out: every contract reference and every future procedure would have to be path-agnostic, and adopters would lose a single predictable convention.

## Decision

The knowledge tree lives under `docs/` — `docs/consumer/`, `docs/contributor/` — and the always-on contract stays at the repository root.
Per-directory contracts travel with their directories.
Adoption is one copy: a root contract plus a `docs/` tree land in place together.
This repository uses the same layout it prescribes.
