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

## 1. The knowledge base describes a settings screen, maps and a difficulty setting that the game does not have

**Answer first — it affects several other topics.** `architecture.md` and `conventions.md` state
that maps change only the background, that difficulty is a separate setting, and that picking a map
in Settings has to redraw the screen. The game on the main branch has **no settings screen, no
maps and no difficulty setting** at all.

What the history shows: a commit "settings menu and new canvas added" adds roughly 200 lines to the
game. It sits on the `knowledge/init` branch, committed after that branch's pull request had already
been merged, so the code was pushed but never reached the main branch. The notes about it were merged
separately.

Is the settings / maps / difficulty feature (a) intended, so the code needs merging into main, or
(b) dropped, in which case the notes should be corrected? If restored, is difficulty a player-facing choice, and what does it change?

Raised by: knowledge-bootstrap (2026-11-06)
_related: index.html, docs/knowledge/architecture.md, docs/knowledge/conventions.md, docs/knowledge/gotchas.md_

## 2. Who is this for, and what is it for?

Nothing in the repository states the audience, the goal, or what success looks like. The design
implies a casual pick-up-and-play game with no onboarding and no account, playable on desktop and
touch. Is that right? Is this a product, a demo, a prototype or a learning exercise?

Raised by: knowledge-bootstrap (2026-11-06)
_related: docs/knowledge/overview.md_

## 3. Are the current balance numbers intended, or placeholders?

Every value below is what the game does today. Please confirm each, or give the intended value.

- Start with **3 lives**, capped at **5**.
- **2 seconds** of invulnerability at the start of a run and after each hit.
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
- The player can fire at most **once every 0.18 seconds**.

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
