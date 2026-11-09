---
audience: technical
owner: Developers
---
# Conventions

<!--
One topic per file. Keep it current: replace outdated statements instead of adding new ones.
Each entry is one of: Decision (and why), Gotcha, Rejected approach (and why), Convention.
Put "_Updated YYYY-MM-DD by <name> — related: <paths>_" under each section you change.
-->

## Visual style

- Background scenery (e.g. asteroids) stays dim and grey. Bright, saturated colours are reserved for things that can hit you: enemies, bullets, power-ups. Why: scenery that looks like an enemy makes players dodge harmless things.
- The palette is a small fixed set of hex literals, written inline at each use — there are no CSS
  custom properties or shared colour constants, and the same colour appears in both the stylesheet
  and the canvas drawing code. Each colour carries meaning: cyan is the player, pink is enemy fire
  and lives, green is the spread shot, and each enemy type owns its own colour, which its explosion
  reuses. Changing a colour means changing every literal for it, so search the whole file.
- Every player ship stays in **cyan or blue tones** and is told apart by its **shape**, not its
  colour. Why: cyan means "the player", and the other bright colours already belong to enemies,
  enemy fire and power-ups — a pink or orange ship would read as an enemy.

_Updated 2026-11-09 by shubham shetmandrekar — related: index.html_

