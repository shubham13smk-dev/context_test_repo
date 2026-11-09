---
audience: business
owner: PM
---
# Open questions

<!--
Questions waiting for a decision, and assumptions that need confirming. Each entry: the question, who raised it, and what the code currently assumes. Remove an entry once it's answered and the answer is recorded in the right topic.
Keep it current: replace outdated statements instead of adding new ones.
Put "_Updated YYYY-MM-DD by <name> — related: <paths>_" under each section you change.
-->

Grouped so they can be answered in one sitting. Once a question is answered, record the answer in
the right topic, remove the matching ⚠ flag there, and delete the entry here.

## 1. Should Easy start at the 5-life cap? — for the PM / BA

On Easy a run starts with 5 lives, which is also the maximum. So an extra-life pickup gives nothing
until the player has been hit at least once. Is that intended? If not, should Easy start lower, or
should the cap be higher on Easy?

Raised by: shubham shetmandrekar (2026-11-07)
_related: index.html, docs/knowledge/business-rules.md_

## 2. Who is this for, and what is it for?

Nothing in the repository states the audience, the goal, or what success looks like. The design
implies a casual pick-up-and-play game with no onboarding and no account, playable on desktop and
touch. Is that right? Is this a product, a demo, a prototype or a learning exercise?

Raised by: knowledge-bootstrap (2026-11-06)
_related: docs/knowledge/overview.md_

## 3. Are the current balance numbers intended, or placeholders?

Every value below is what the game does today. Please confirm each, or give the intended value.

- Start with **5 / 3 / 2 lives** on Easy / Normal / Hard, capped at **5** (see question 1).
- **2 seconds** of invulnerability at the start of a run and after each hit (after a hit this
  depends on the ship — see question 11).
- Being hit **cancels the spread shot**, even with time left on it.
- Enemies are worth **10 / 25 / 50** points.
- An enemy escaping off the bottom costs **5 points**, and the score is floored at **0**.
- The level rises **every 20 seconds**, on a timer, regardless of how the player is doing.
- The enemy mix unlocks at **level 2** and **level 4**; within what is unlocked, each type is
  equally likely.
- Enemies get **12% faster per level with no cap**, so a long run eventually becomes unplayable.
  Is an upper limit wanted?
- Spawn rate floors at about **0.3s**; the shooting enemy's fire rate floors at **0.8s**.
- **8% drop chance** per enemy, the same for every enemy type, split **50/50** between spread shot
  and extra life.
- The spread shot lasts **8 seconds**, and collecting another **resets** rather than extends it.
- The Falcon can fire at most **once every 0.18 seconds** (other ships: see question 11).

Raised by: knowledge-bootstrap (2026-11-06)
_related: index.html, docs/knowledge/business-rules.md_

## 4. Is "hold to move also fires" intended on touch and mouse?

On touch and mouse the player cannot move without shooting — the same press does both. On keyboard
the two are separate. Intended simplification, or a side effect to fix?

Raised by: knowledge-bootstrap (2026-11-06)
_related: index.html_

## 5. Is losing points for escaped enemies meant to be visible?

An enemy reaching the bottom silently removes 5 points. There is no sound, flash or message, so a
player can lose points without noticing why. Should there be feedback?

Raised by: knowledge-bootstrap (2026-11-06)
_related: index.html_

## 6. Which absent features are deliberate?

None of these exist today. For each: deliberately out of scope, or simply not built yet?

- Accounts and online leaderboards. The best score is kept only in the player's own browser and is
  lost if they clear site data or change device or browser.
- Saving a run in progress.
- Sound and music — the game is completely silent.
- A win condition, an ending, or boss fights. Runs only end by losing.
- Designed waves or stages, as opposed to the current time-driven difficulty ramp.

Raised by: knowledge-bootstrap (2026-11-06)
_related: index.html, docs/knowledge/features-and-scope.md_

## 7. Is there a roadmap?

Nothing in the repository records what is planned next. If there is a backlog or ticket tracker,
where does it live, so `features-and-scope.md` can link to it?

Raised by: knowledge-bootstrap (2026-11-06)
_related: docs/knowledge/features-and-scope.md_

## 8. How is the game meant to be published? — for the developers

There is no build, no CI, no hosting configuration and no deployment script in the repository, so
`deployment.md` is empty. Is the game published anywhere today? If so, how does a change reach it?

Raised by: knowledge-bootstrap (2026-11-06)
_related: docs/knowledge/deployment.md_

## 9. Should there be automated tests? — for the developers

There are no tests of any kind, and no test tooling. The balance rules above are the kind of thing
that is easy to break silently. Is testing wanted, and at what level?

Raised by: knowledge-bootstrap (2026-11-06)
_related: docs/knowledge/known-issues.md_

## 10. Does the game need to support small screens properly?

The playfield is a fixed 480×640 and is only scaled down by the browser to fit. There is no
re-layout, no portrait/landscape handling and no on-screen control hints after the opening screen.
Is "scaled to fit" good enough for mobile?

Raised by: knowledge-bootstrap (2026-11-06)
_related: index.html_

## 11. Are the ship stats and unlock scores intended? — for the PM / BA

The six ships and their unlock thresholds (300 / 600 / 1000 / 1600 / 2500) were proposed by the
developer, not specified. The full table is under "Ships" in business-rules.md. Please confirm or
adjust, in particular:

- Is any ship clearly better than the Falcon at everything? (Intended: each one trades something.)
- Are the thresholds reachable for a casual player? The top ship needs a 2500-point run.
- Should unlocks be tied to the high score at all, or to something else (e.g. total play)?

Raised by: shubham shetmandrekar (2026-11-09)
_related: index.html, docs/knowledge/business-rules.md_

## 12. Should high scores be ranked per difficulty? — for the PM / BA

The High Scores screen keeps one top-5 list for all difficulties, so an Easy run and a Hard run
compete directly. Each entry shows its difficulty. Should there be a separate list per difficulty,
or a single list as today? Relatedly: should 0-point runs stay unrecorded?

Raised by: shubham shetmandrekar (2026-11-09)
_related: index.html, docs/knowledge/business-rules.md_
