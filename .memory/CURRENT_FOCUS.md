# CURRENT_FOCUS

## One-liner
- Ark Station: A crisis management survival game - maintain governance-only memory for Claude Code sessions.

## Active Objectives (max 3)
1. Continue development of Ark Station game
2. (add more as needed)

## Next Actions
- [x] Remove unused DEATH_MESSAGES constant (dead code cleanup)
- [x] Change tick rate to 5 ticks/sec with same overall pacing
- [ ] Test game end-to-end with new tick rate
- [ ] Consider adding cause-of-death variety beyond "Pod failure"

## Open Loops / Blockers
- None

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
- Changed tick rate from 3000ms to 200ms (5 ticks/second)
- Divided all per-tick rates by 15 to maintain same real-time pacing
- Multiplied all tick counts by 15 (solar flare timing, research costs)
- Added MAX_STASIS_POWER cap of 5 for life support system
- Death rate display now always visible, shows "−X.X/sec" format
- Adjusted baseDeaths to 0.741 so 5 power + 20% integrity = 1 death/sec
- Death rate calculated in updateUI so it updates even when paused

## Pinned References
- Governance rules: `CLAUDE.md`
- Game changelog: `CHANGELOG.md`

Hard rule: If "Key Context" becomes a wall of text, move it into real docs and link here.
