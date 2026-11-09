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
- Full-screen panels (Settings, High Scores, Hangar) all open and close through `showPanel` /
  `closePanel`, which track the single open panel in `openPanel`; Escape closes whichever is open.
  A new panel must use these, not its own `xOpen` flag. Why: with per-panel flags every panel had to
  be wired into the Escape handler by hand, and a merge left that handler calling a removed
  function, so every key press threw an error.

_Updated 2026-11-09 by shubham shetmandrekar — related: index.html_

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
- The title-screen loop (`menuLoop`) stops itself as soon as the state leaves `menu`. Anything that
  returns to the title screen (today: Exit from pause) must call `menuLoop()` again, or the title
  background stays frozen.

_Updated 2026-11-09 by shubham shetmandrekar — related: index.html_

## Entities and collisions

- Every entity kind (bullets, enemies, enemy bullets, particles, power-ups, stars) is a plain array
  of plain objects. Nothing is a class, and there is no entity id or pooling.
- Despawning is done by reassigning the array from a `filter` each frame rather than splicing in
  place, so the arrays are `let` bindings, not `const`.
- Enemy types are defined in one table of literals (hit points, radius, speed, colour, points,
  whether it shoots), and a spawned enemy is a shallow copy of its table entry with per-instance
  fields added. Changing a type's balance means changing that table.
- Player ships work the same way: one `SHIPS` table holds each ship's stats, shape points, colour
  and unlock score, and the running `player` keeps a reference to its ship. Changing a ship's
  balance or adding a ship means changing that table only; the Hangar reads it to draw cards and
  stat bars.
- All collisions are circle-distance checks. Each ship's hit radius is deliberately smaller than
  its drawn shape, which is the usual forgiving-hitbox trick.

_Updated 2026-11-09 by shubham shetmandrekar — related: index.html_

## Persistence

- Three things are saved in local storage: the high score (`starBlasterHigh`), the top 5 scores
  (`starBlasterScores`) and the player's settings (map, change map each level, difficulty,
  auto-fire, selected ship). Every read and write is wrapped in `try`/`catch`, so the game still
  runs where storage is unavailable or blocked; all then reset each session.
- `starBlasterHigh` is still written alongside the top-5 list, and a best score saved before the
  list existed is seeded as its first entry. Why: older players keep their best score, and ship
  unlocks keep reading `highScore` unchanged.
- That seeded entry has `level` and `difficulty` set to `null` (they were never saved). The loader
  must accept `null` there, or the old best score is filtered out and silently lost on the next
  reload.
- Saved settings are checked against the list of valid options when loaded. Any unknown or invalid
  value falls back to the default, so a renamed or removed option never breaks the game.
- The saved ship is also checked against the high score, on load and again when a run starts. A
  ship that is no longer unlocked (e.g. the high score was cleared) falls back to the Falcon rather
  than being playable while locked.

_Updated 2026-11-09 by shubham shetmandrekar — related: index.html_

