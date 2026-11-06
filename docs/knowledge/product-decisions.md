---
audience: business
owner: PM
---
# Product decisions

<!--
Product-level choices and why they were made (what was chosen, what was rejected). Technical decisions go in architecture.md.
Keep it current: replace outdated statements instead of adding new ones.
Put "_Updated YYYY-MM-DD by <name> — related: <paths>_" under each section you change.
-->

Only two decisions are recorded anywhere in the repository with their reasoning, and both are
already written up in technical topics. They are listed here as pointers so a PM reading this file
first does not miss them; the linked file stays the source of truth.

## Recorded elsewhere

- **Maps affect the background only, never gameplay** — the reason is in
  [architecture.md](architecture.md) under "Maps / backgrounds". Note that no maps exist in the
  game on the main branch today; see [open-questions.md](open-questions.md).
- **Bright colours are reserved for things that can hit the player; scenery stays dim and grey** —
  the reason is in [conventions.md](conventions.md) under "Visual style".

Nothing else in the code, comments, commit messages or docs states *why* a product choice was made,
so nothing else is recorded here. Everything the code merely *does* is in
[business-rules.md](business-rules.md), with the open ones listed in
[open-questions.md](open-questions.md).

_Drafted 2026-11-06 by knowledge-bootstrap — related: docs/knowledge/architecture.md, docs/knowledge/conventions.md_
