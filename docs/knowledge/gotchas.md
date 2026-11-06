# Gotchas

<!--
One topic per file. Keep it current: replace outdated statements instead of adding new ones.
Each entry is one of: Decision (and why), Gotcha, Rejected approach (and why), Convention.
Put "_Updated YYYY-MM-DD by <name> — related: <paths>_" under each section you change.
-->

## Rendering

- The canvas only redraws continuously while playing or on the start menu. On the pause and game-over screens it stays frozen on the last frame, so any visual change made there (e.g. picking a map in Settings) must call `draw()` itself.

_Updated 2026-11-06 by shubham shetmandrekar — related: index.html_

## Testing

- The Playwright browser tool blocks `file://` URLs. Serve the folder over a local web server (e.g. `python -m http.server`) and open it at `http://localhost:<port>/index.html`.

_Updated 2026-11-06 by shubham shetmandrekar — related: index.html_

