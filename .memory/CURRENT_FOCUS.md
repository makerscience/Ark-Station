# CURRENT_FOCUS

## One-liner
- Ark Station: A crisis management survival game - maintain governance-only memory for Claude Code sessions.

## Active Objectives (max 3)
1. Continue development of Ark Station game
2. (add more as needed)

## Next Actions
- [ ] Review current game state and identify next development priorities
- [ ] (add more as needed)

## Open Loops / Blockers
- None yet

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
- Added game clock display showing "Month Day, HH:MM, Year" format
- Game starts at October 17, 00:00, 3326
- Ticks every 10 seconds, advancing 10 minutes of game time per tick
- All rates (decay, damage, repair, deaths) reduced by 6x to maintain same real-time pace
- Added fractional death accumulator for sub-integer death calculations
- Clock resets properly on game restart

## Pinned References
- Governance rules: `CLAUDE.md`
- Game changelog: `CHANGELOG.md`

Hard rule: If "Key Context" becomes a wall of text, move it into real docs and link here.
