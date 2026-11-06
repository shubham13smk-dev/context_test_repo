---
audience: technical
owner: Developers
---
# Architecture

<!--
One topic per file. Keep it current: replace outdated statements instead of adding new ones.
Each entry is one of: Decision (and why), Gotcha, Rejected approach (and why), Convention.
Put "_Updated YYYY-MM-DD by <name> — related: <paths>_" under each section you change.
-->

## Maps / backgrounds

- **Decision:** maps change only the background. They have no effect on gameplay (no obstacles, no collisions, no change to enemies). Why: "Change map each level" swaps maps every level, so balance must be identical on every map. Difficulty is a separate setting.

_Updated 2026-11-07 by shubham shetmandrekar — related: index.html_

## Shape of the whole thing

- One file, `index.html`, holds the markup, the styles and the entire game. No build step, no
  dependencies, no modules, no framework. A change is a page reload away.
- The playfield is a fixed 480×640 2D canvas. Overlay screens (title, paused, game over) are plain
  DOM on top of the canvas rather than drawn into it, so they get real buttons and HTML text.

_Drafted 2026-11-06 by knowledge-bootstrap — related: index.html_

## State machine and the loop

- A single `state` variable drives everything: `menu`, `playing`, `paused`, `over`. The main loop
  returns immediately unless the state is `playing`, and a separate small loop animates the
  starfield behind the title screen.
- The loop is `requestAnimationFrame` with a real delta time, so motion is frame-rate independent,
  but `dt` is clamped at 0.033s. A stalled frame therefore slows the game down rather than
  teleporting entities through each other — deliberate, since collisions are point checks with no
  sweeping.
- Pausing and resuming resets the loop's time reference, so time spent paused does not count
  towards the level timer or any cooldown.

_Drafted 2026-11-06 by knowledge-bootstrap — related: index.html_

## Entities and collisions

- Every entity kind (bullets, enemies, enemy bullets, particles, power-ups, stars) is a plain array
  of plain objects. Nothing is a class, and there is no entity id or pooling.
- Despawning is done by reassigning the array from a `filter` each frame rather than splicing in
  place, so the arrays are `let` bindings, not `const`.
- Enemy types are defined in one table of literals (hit points, radius, speed, colour, points,
  whether it shoots), and a spawned enemy is a shallow copy of its table entry with per-instance
  fields added. Changing a type's balance means changing that table.
- All collisions are circle-distance checks. The player's hit radius (14) is deliberately smaller
  than its drawn ship, which is the usual forgiving-hitbox trick.

_Drafted 2026-11-06 by knowledge-bootstrap — related: index.html_

## Persistence

- Two things are saved in local storage: the high score and the player's settings (map, change map
  each level, difficulty, auto-fire). Every read and write is wrapped in `try`/`catch`, so the game
  still runs where storage is unavailable or blocked; both then reset each session.
- Saved settings are checked against the list of valid options when loaded. Any unknown or invalid
  value falls back to the default, so a renamed or removed option never breaks the game.

_Updated 2026-11-07 by shubham shetmandrekar — related: index.html_

