# CURRENT_FOCUS

## One-liner
- Ark Station: A crisis management survival game - maintain governance-only memory for Claude Code sessions.

## Active Objectives (max 3)
1. Continue development of Ark Station game
2. Playtest and balance gameplay

## Next Actions
- [ ] Playtest full game loop from intro to victory/defeat
- [ ] Balance decay/repair rates if game feels too fast or slow
- [ ] Add scientific names for shield repair upgrades (currently placeholders)
- [ ] Add more variety to ending messages based on victory conditions
- [ ] Consider individual drone assignment system (explored but deferred)

## Open Loops / Blockers
- Shield repair upgrades have placeholder names ("Solar Shield: Repair Enhancement I/II/III")
- Display power cost for solar/orbital panels not implemented

## How to Resume in 30 Seconds
- **Open:** `.memory/CURRENT_FOCUS.md`
- **Next:** Execute the first unchecked item in "Next Actions"
- **If unclear:** Run "Follow the Session Start Protocol"

## Key Context
- Memory files: `.memory/CURRENT_FOCUS.md`, `.memory/DECISIONS.md`
- Changelog: `CHANGELOG.md`
- How to start session: "Follow the Session Start Protocol"
- How to end session: "Do the Session End Protocol"
- Main game file: `index.html`
- Design document: `Ark Station — Crisis Management Survival Game Design Document.pdf`

---

## Last Session Summary (max ~8 bullets)
- Added "Skip Intro + Tutorials" button to intro screen
- Implemented 6 tutorial popups: stasis unlock, first flare, CA4, very close zone, orbital status, deaths stabilized
- Tutorial modals can only be closed via button (no background click dismiss)
- Solar Shield Matrix text now bright green when online
- All tutorials respect `skipAllTutorials` flag

## Pinned References
- Governance rules: `CLAUDE.md`
- Game changelog: `CHANGELOG.md`

Hard rule: If "Key Context" becomes a wall of text, move it into real docs and link here.
