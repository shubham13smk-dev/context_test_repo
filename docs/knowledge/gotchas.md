---
audience: technical
owner: Developers
---
# Gotchas

<!--
One topic per file. Keep it current: replace outdated statements instead of adding new ones.
Each entry is one of: Decision (and why), Gotcha, Rejected approach (and why), Convention.
Put "_Updated YYYY-MM-DD by <name> — related: <paths>_" under each section you change.
-->

## Rendering

- The canvas only redraws continuously while playing or on the start menu. On the pause and game-over screens it stays frozen on the last frame, so any visual change made there (e.g. picking a map in Settings) must call `draw()` itself.
- Overlay panels (title, Settings, High Scores, Hangar) sit inside the canvas-sized wrapper, and
  the canvas shrinks to fit short browser windows. A tall panel then spills out and its title and
  Back button are cut off. Every panel therefore scrolls (`overflow-y: auto` with
  `justify-content: safe center`; the shared `.panel` class gives this to Settings and High
  Scores). Test new panels in a short window (e.g. 500px high), not only full screen.

_Updated 2026-11-09 by shubham shetmandrekar — related: index.html_

## Testing

- The Playwright browser tool blocks `file://` URLs. Serve the folder over a local web server (e.g. `python -m http.server`) and open it at `http://localhost:<port>/index.html`.
- Playwright only saves screenshots inside the repo (outside paths are refused). Save them under
  `.playwright-mcp/`, which is git-ignored so test output never gets committed.

_Updated 2026-11-09 by shubham shetmandrekar — related: index.html, .gitignore_

## Timing

- `dt` is clamped at 0.033s (≈30fps). Below that frame rate the game runs in slow motion instead of
  dropping frames — so a performance problem shows up as sluggish play, not as missed collisions.
  Don't "fix" an apparent speed bug without checking the frame rate first.

_Drafted 2026-11-06 by knowledge-bootstrap — related: index.html_

## Input

- `keydown` calls `preventDefault()` for space and the arrow keys, so the page never scrolls during
  play. Any new key that the browser also acts on needs adding to that list.
- The pointer handlers are split deliberately: `pointerdown` and `pointermove` are on the canvas,
  but `pointerup` is on the window. If `pointerup` moves onto the canvas, releasing outside it
  leaves the ship stuck moving and auto-firing.

_Drafted 2026-11-06 by knowledge-bootstrap — related: index.html_

