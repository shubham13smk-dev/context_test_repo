---
audience: technical
owner: Developers
---
# Getting started

<!--
How to run, test and debug the project locally. Only the steps that aren't obvious.
Keep it current: replace outdated statements instead of adding new ones.
Put "_Updated YYYY-MM-DD by <name> — related: <paths>_" under each section you change.
-->

## Running it

- There is nothing to install and nothing to build: no package manager, no dependencies, no
  bundler. Open `index.html` in a browser and the game runs.
- To serve it instead (needed for browser automation, see gotchas.md), run any static server from
  the repo root, e.g. `python -m http.server`, and open `http://localhost:8000/index.html`.

_Drafted 2026-11-06 by knowledge-bootstrap — related: index.html_

## Editing

- Everything — markup, styles and the whole game — is in `index.html`. There is no source tree and
  no watch process; reload the page to see a change.
- The game uses two local-storage keys: `starBlasterHigh` (high score) and `starBlasterSettings`
  (map, difficulty, auto-fire). Clear **both** to test a true first run — clearing only the high
  score leaves the saved settings in place.

_Updated 2026-11-09 by shubham shetmandrekar — related: index.html_

## Testing

- There are no automated tests and no test tooling in the repository. Changes are verified by
  playing the game. See known-issues.md.

_Drafted 2026-11-06 by knowledge-bootstrap — related: index.html_
