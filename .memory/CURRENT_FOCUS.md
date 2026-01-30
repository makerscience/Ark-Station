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
- Fixed Repair Drone panel layout issue
- Converted from flexbox to absolute positioning for targets row, drone hub, and power section
- Root cause: `.drone-visual-container` was 160px but panel was locked at 271px
- Fix: Increased container height to 235px to fill the panel
- Targets row now at top, power section at bottom, drone hub in middle

## Pinned References
- Governance rules: `CLAUDE.md`
- Game changelog: `CHANGELOG.md`

Hard rule: If "Key Context" becomes a wall of text, move it into real docs and link here.
