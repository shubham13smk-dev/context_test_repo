---
audience: technical
owner: Developers
---
# Known issues

<!--
Known limitations and tech debt, and why they haven't been fixed yet.
Keep it current: replace outdated statements instead of adding new ones.
Put "_Updated YYYY-MM-DD by <name> — related: <paths>_" under each section you change.
-->

## No tests

There are no tests and no test tooling. Every balance rule in business-rules.md is a bare literal in
one file, so any of them can be changed or broken without anything noticing. See question 9 in
open-questions.md.

_Drafted 2026-11-06 by knowledge-bootstrap — related: index.html_

## A spent player bullet is "removed" by teleporting it off-screen

When a bullet hits an enemy, it is not removed from the list directly — it is moved far above the
top of the screen so that the filter on the next line drops it, and the hit effect is drawn by
adding that offset back to get the real position. It works, but it is easy to break: anything that
reads a bullet's position between the hit and the filter sees a bogus value, and the two offsets
have to stay in step.

_Drafted 2026-11-06 by knowledge-bootstrap — related: index.html_

## Enemy speed scales without a cap

Enemy speed is multiplied per level with no upper limit, so a long enough run becomes unplayable
rather than merely hard. The spawn rate and enemy fire rate both have floors; speed does not.
Whether this is intended is question 3 in open-questions.md.

_Drafted 2026-11-06 by knowledge-bootstrap — related: index.html_

## Fixed playfield size

The playfield is a fixed 480×640 canvas, scaled down by CSS to fit the viewport. There is no
re-layout for small or landscape screens, and the control hints disappear with the opening screen.
See question 10 in open-questions.md.

_Drafted 2026-11-06 by knowledge-bootstrap — related: index.html_

## README is effectively empty

`README.md` contains only the repository name, and is encoded as UTF-16 with a byte-order mark, so
it renders with stray characters in some tools. It tells a newcomer nothing.

_Drafted 2026-11-06 by knowledge-bootstrap — related: README.md_
