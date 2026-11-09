---
audience: business
owner: BA
---
# Business rules

<!--
Rules the product must follow (calculations, limits, eligibility, game rules…), each with the reason. Code shows how a rule is implemented; this file says what the rule is meant to be.
Keep it current: replace outdated statements instead of adding new ones.
Put "_Updated YYYY-MM-DD by <name> — related: <paths>_" under each section you change.
-->

The values below are what the game does today, read from the code. Unless a reason is stated, the
reason is ⚠ **Needs PM/BA confirmation** and the value is listed in open-questions.md as
"is this intended?".

## Lives and damage

- A run starts with **5 lives on Easy, 3 on Normal, 2 on Hard**. Changing difficulty mid-run does
  not change the current lives; it applies from the next run.
- The player loses **one life** per hit, whether hit by an enemy's shot or by colliding with an
  enemy. Colliding also destroys that enemy.
- The run ends as soon as lives reach **zero**.
- For the first **2 seconds** of a run, and after being hit, the player cannot be hit again. The
  time after a hit depends on the ship: **2 seconds**, except the Phantom at **3.5 seconds**. The
  ship blinks for the whole of that time so the state is visible.
- How easily the player is hit depends on the ship's hitbox (see Ships).
- Being hit also **cancels the three-way shot** immediately, even if time was left on it.
- Lives are capped at **5**. Collecting an extra life at 5 lives gives nothing back. On Easy a run
  starts at the cap. ⚠ Needs PM/BA confirmation — see question 1 in open-questions.md.

_Updated 2026-11-09 by shubham shetmandrekar — related: index.html_

## Scoring

- Destroying an enemy scores **10** (weak), **25** (weaving) or **50** (shooting) points.
- An enemy that escapes off the bottom of the screen costs the player **5 points**.
- The score can never go **below zero** — a penalty at zero points costs nothing.
- The highest score ever reached in that browser is kept and shown at the end of a run. It is
  stored on the player's own device only.

_Drafted 2026-11-06 by knowledge-bootstrap — related: index.html_

## Levels and difficulty

- The level goes up **every 20 seconds of play**, regardless of how well the player is doing.
  Paused time does not count. There is no upper level.
- The enemy mix is unlocked by level: **level 1** has only the weak enemy; **levels 2–3** add the
  weaving enemy; **level 4 onward** adds the shooting enemy. Within what is unlocked, each spawn
  picks a type at random with equal chance.
- Enemies move **12% faster per level** above level 1, and this increase is **never capped**.
- Enemies spawn more frequently as the level rises, down to a **floor of roughly one spawn every
  0.3 seconds** on average on Normal. The difficulty multiplier is applied *after* the floor, so
  the effective floor is about **0.39s on Easy and 0.225s on Hard**.
- The shooting enemy fires faster as the level rises, down to a **floor of one shot every
  0.8 seconds**. It only fires once it is on screen.
- On top of the level ramp, the chosen difficulty scales enemy pressure: enemy speed is
  **×0.8 on Easy, ×1 on Normal, ×1.25 on Hard**, and the time between spawns is **×1.3 / ×1 / ×0.75**.
  A change of difficulty mid-run takes effect immediately for these.

_Updated 2026-11-09 by shubham shetmandrekar — related: index.html_

## Power-ups

- Each destroyed enemy has an **8% chance** of dropping a power-up. The drop chance is the same for
  every enemy type, so weak enemies drop just as often as tough ones.
- A dropped power-up is a **50/50** chance of the three-way shot or an extra life.
- The three-way shot lasts **8 seconds**. Collecting another one while it is active **resets it to
  8 seconds** rather than adding to it.
- Power-ups fall at a fixed speed and are lost if they reach the bottom uncollected.

_Drafted 2026-11-06 by knowledge-bootstrap — related: index.html_

## Firing

- The fire rate depends on the ship (see Ships). The Falcon fires at most **once every
  0.18 seconds**, held or tapped — no ship can fire faster than its own rate.
- With the three-way shot active, each of the ship's cannons fires **three bullets** in a narrow
  fan instead of one (so the Twin fires six).
- On touch and mouse, holding down to move also fires. The player **cannot move without shooting**
  on touch. ⚠ Needs PM/BA confirmation — intended, or a side effect?
- On keyboard, firing is manual by default. With **Auto-fire** on in Settings, the ship fires
  continuously at the ship's normal rate without holding space.

_Updated 2026-11-09 by shubham shetmandrekar — related: index.html_

## Ships

The player picks one of six ships in the Hangar. Ships play differently so that the choice matters.
The Falcon keeps the original stats, so the default game plays exactly as before.

| Ship | Unlocks at high score | Speed | Time between shots | Damage per bullet | Hit radius | Invulnerable after hit |
|---|---|---|---|---|---|---|
| Falcon | 0 (default) | 320 | 0.18s | 1 | 14 | 2s |
| Dart | 300 | 430 | 0.24s | 1 | 10 | 2s |
| Twin (2 cannons) | 600 | 290 | 0.24s | 1 | 16 | 2s |
| Bulwark | 1000 | 240 | 0.30s | 2 | 18 | 2s |
| Stinger | 1600 | 270 | 0.11s | 1 | 14 | 2s |
| Phantom | 2500 | 340 | 0.20s | 1 | 13 | 3.5s |

- A ship is **unlocked once the best score in that browser reaches its threshold**, and stays
  unlocked while that high score is kept. If the high score is cleared, a selected ship that is no
  longer unlocked falls back to the Falcon.
- The ship **cannot be changed during a run**. The Hangar opens only from the opening and game-over
  screens, not from pause. Why: swapping stats mid-run would let a player switch ships to suit the
  moment, e.g. to the Phantom just before taking a hit.
- When a run raises the high score past a threshold, the game-over screen says which ship was
  unlocked.
- ⚠ Needs PM/BA confirmation: all stats and thresholds were proposed by the developer. See
  question 11 in open-questions.md.

_Updated 2026-11-09 by shubham shetmandrekar — related: index.html_
