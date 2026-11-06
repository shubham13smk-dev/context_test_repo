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

- A run starts with **3 lives**.
- The player loses **one life** per hit, whether hit by an enemy's shot or by colliding with an
  enemy. Colliding also destroys that enemy.
- The run ends as soon as lives reach **zero**.
- After being hit, and for the first **2 seconds** of a run, the player cannot be hit again. The
  ship blinks for the whole of that time so the state is visible.
- Being hit also **cancels the three-way shot** immediately, even if time was left on it.
- Lives are capped at **5**. Collecting an extra life at 5 lives gives nothing back.

_Drafted 2026-11-06 by knowledge-bootstrap — related: index.html_

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
  0.3 seconds** on average.
- The shooting enemy fires faster as the level rises, down to a **floor of one shot every
  0.8 seconds**. It only fires once it is on screen.

_Drafted 2026-11-06 by knowledge-bootstrap — related: index.html_

## Power-ups

- Each destroyed enemy has an **8% chance** of dropping a power-up. The drop chance is the same for
  every enemy type, so weak enemies drop just as often as tough ones.
- A dropped power-up is a **50/50** chance of the three-way shot or an extra life.
- The three-way shot lasts **8 seconds**. Collecting another one while it is active **resets it to
  8 seconds** rather than adding to it.
- Power-ups fall at a fixed speed and are lost if they reach the bottom uncollected.

_Drafted 2026-11-06 by knowledge-bootstrap — related: index.html_

## Firing

- The player can fire at most **once every 0.18 seconds**, held or tapped — firing faster is not
  possible.
- With the three-way shot active, one shot fires **three bullets** in a narrow fan instead of one.
- On touch and mouse, holding down to move also fires. The player **cannot move without shooting**
  on touch. ⚠ Needs PM/BA confirmation — intended, or a side effect?

_Drafted 2026-11-06 by knowledge-bootstrap — related: index.html_
