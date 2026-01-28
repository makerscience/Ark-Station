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
- Implemented 5-zone proximity system: Far/Medium/Close/Very Close/Critical (boundaries 80/60/40/20)
- Added red vignette overlay + ambient warning messages for Roche limit foreshadowing
- Zone-scaled solar flares: frequency, duration, and damage scale with proximity
- Shield now reduces radiation damage (up to 50%) and dampens vignette overlay
- Added ambient temperature readout in shield panel (appears at CA4, 150K→4000K curve)
- Orbital distance progression: CA2=90(FAR), CA3=70(MEDIUM), CA4=50(CLOSE, decay starts)
- Thruster rebalance: 2=stable, 3=climb, 4=fast climb; research extended to 8 levels
- Renamed "Casualty Log" to "System Log"

## Pinned References
- Governance rules: `CLAUDE.md`
- Game changelog: `CHANGELOG.md`

Hard rule: If "Key Context" becomes a wall of text, move it into real docs and link here.
