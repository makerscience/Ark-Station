# CURRENT_FOCUS

## One-liner
- Ark Station: A crisis management survival game - maintain governance-only memory for Claude Code sessions.

## Active Objectives (max 3)
1. Continue development of Ark Station game
2. (add more as needed)

## Next Actions
- [ ] Test game end-to-end with new phase progression system
- [ ] Verify panels appear/hide correctly at each CA level
- [ ] Balance solar flare timing and damage values
- [ ] Consider adding display power cost mechanic (solar/orbital panels costing 1 power each)

## Open Loops / Blockers
- Display power cost not yet implemented (plan mentioned it but skipped for now)

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
- Implemented 5-phase game progression system tied to Command Authorization levels
- Solar flare timing reduced to 2-4 minutes (was 4.5-36 minutes)
- Added power caps of 5 to all systems (stasis, drones, shield, thrusters)
- Restructured research tree from 16 to 32 upgrades with system unlock gates
- Added orbital movement indicator showing direction (climbing/falling/stable) and speed
- Implemented UI visibility system - panels hidden until researched
- Made solar flares only active after CA Level 2, orbital decay after CA Level 3
- Power progression now 5→8→11→14→17→20 via 5 reactor upgrades

## Pinned References
- Governance rules: `CLAUDE.md`
- Game changelog: `CHANGELOG.md`

Hard rule: If "Key Context" becomes a wall of text, move it into real docs and link here.
