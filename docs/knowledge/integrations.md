---
audience: technical
owner: Developers
---
# Integrations

<!--
External services, APIs and data sources: what each is used for, who owns it, and where its credentials live (never the credentials themselves).
Keep it current: replace outdated statements instead of adding new ones.
Put "_Updated YYYY-MM-DD by <name> — related: <paths>_" under each section you change.
-->

## None

The game makes no network requests. There are no external services, APIs, CDNs, fonts, analytics or
data sources, and no credentials or environment variables of any kind. Everything it needs is in
`index.html`.

The only browser APIs it depends on are the 2D canvas, pointer events, `requestAnimationFrame`, and
local storage (for the high score — see getting-started.md). Local storage access is wrapped so the
game still runs where storage is blocked, such as a private window.

_Drafted 2026-11-06 by knowledge-bootstrap — related: index.html_
