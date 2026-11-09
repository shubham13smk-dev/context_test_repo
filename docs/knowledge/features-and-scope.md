---
audience: business
owner: PM
---
# Features and scope

<!--
What the product does today, what is deliberately out of scope (and why), and what is planned next. Link tickets instead of copying them.
Keep it current: replace outdated statements instead of adding new ones.
Put "_Updated YYYY-MM-DD by <name> — related: <paths>_" under each section you change.
-->

## In the product today — playing

- A single endless run: enemies keep coming until the player runs out of lives.
- The ship moves left and right only, along the bottom of the screen. It cannot move up or down.
- Shooting is manual on keyboard (unless auto-fire is switched on in Settings) and automatic while a
  finger or pointer is held down.
- The run can be paused and resumed at any time while playing.
- A run can be started from the opening screen or restarted from the game-over screen.

_Drafted 2026-11-06 by knowledge-bootstrap — related: index.html_

## In the product today — enemies and difficulty

- Three kinds of enemy, introduced gradually as the run goes on: a fast weak one, a tougher one
  that weaves side to side, and a slow tough one that shoots back at the player.
- The shooting enemy aims at wherever the player currently is.
- Tougher enemies show a small health bar above them, so the player can see what is nearly dead.
- Difficulty rises automatically with the level: enemies arrive faster, move faster, and the
  shooting enemy fires more often.

_Drafted 2026-11-06 by knowledge-bootstrap — related: index.html_

## In the product today — scoring and power-ups

- Points are earned per enemy destroyed, worth more for tougher enemies.
- Points are lost when an enemy escapes off the bottom of the screen.
- Two power-ups can drop from destroyed enemies: a temporary three-way shot, and an extra life.
- The score, the current level and the remaining lives are shown on screen during play.
- The best score reached is kept on the player's own device and shown when a run ends.

_Drafted 2026-11-06 by knowledge-bootstrap — related: index.html_

## In the product today — controls and presentation

- Keyboard: arrow keys or A/D to move, space to shoot, P to pause, Enter or space to start.
- Touch and mouse: drag to move, hold to fire.
- A moving background plays behind the opening screen and during the game. There are four to choose
  from (Deep Space, Nebula, Asteroid Field, Cyber Grid). They are scenery only and never affect play.
- Explosions, engine flame and a blinking ship after being hit give visual feedback.

_Drafted 2026-11-06 by knowledge-bootstrap — related: index.html_

## In the product today — settings

- A Settings screen, reachable from the opening, paused and game-over screens. Choices are
  remembered in the player's browser.
- **Map:** pick one of the four backgrounds, or have the map change every level.
- **Difficulty:** Easy, Normal or Hard. It sets the starting lives and how fast and how often
  enemies come. See business-rules.md.
- **Auto-fire:** keeps the ship shooting on keyboard without holding space. Off by default.

_Updated 2026-11-07 by shubham shetmandrekar — related: index.html_

## In the product today — ships and the Hangar

- Six player ships, each playing differently: Falcon (all-rounder, the default), Dart (fast, small,
  slow-firing), Twin (two cannons, wider), Bulwark (slow, big, double damage), Stinger (rapid fire,
  slower to move) and Phantom (longer invulnerability after a hit). Stats are in business-rules.md.
- New ships unlock as the player's high score grows, so they are a reward for getting better.
- A **Hangar** screen, reachable from the opening and game-over screens, shows every ship with a
  preview and bars for speed, fire rate, damage and evasion. Locked ships show the score they need.
  The chosen ship is remembered in the player's browser.
- The game-over screen announces any ship unlocked by that run.

_Updated 2026-11-09 by shubham shetmandrekar — related: index.html_

## In the product today — high scores

- A **High Scores** screen, reachable from the opening, paused and game-over screens, lists the
  player's 5 best runs on that browser with the level and difficulty of each. The run just played
  is outlined if it made the list. Rules are in business-rules.md.

_Updated 2026-11-09 by shubham shetmandrekar — related: index.html_

## Not in the product

Things a player or reviewer might reasonably expect, which the game does not have today:

- **Accounts or online leaderboards** — the best score never leaves the player's browser, and is
  lost if they clear site data or switch device or browser. ⚠ Deliberate, or not yet built?
- **Saving a run in progress** — closing the page loses the run. ⚠ Deliberate, or not yet built?
- **Sound or music** — the game is completely silent. ⚠ Deliberate, or not yet built?
- **An end, a win condition or boss fights** — runs only end by losing.
  ⚠ Deliberate, or not yet built?
- **Levels as designed waves** — "level" is purely a difficulty step driven by elapsed time; there
  are no hand-built waves or stages. ⚠ Deliberate, or not yet built?

_Drafted 2026-11-06 by knowledge-bootstrap — related: index.html_

## Planned next

_No entries yet._ ⚠ Nothing in the repository records a roadmap. See open-questions.md.

_Drafted 2026-11-06 by knowledge-bootstrap — related: (none)_
